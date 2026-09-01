<script>
/* =========================================
   KHON HAND TRACKING
   Trackpad + Zoom
   ========================================= */

const video = document.getElementById("webcam");
const canvas = document.getElementById("hand-canvas");
const ctx = canvas.getContext("2d");

const statusText = document.getElementById("hand-status");
const website = document.getElementById("website");
const cursor = document.getElementById("gesture-cursor");
const zoomValue = document.getElementById("zoom-value");


/* =========================================
   SETTINGS
   ========================================= */

const MIN_ZOOM = 0.75;
const MAX_ZOOM = 1.70;

let zoom = 1;

let previousIndexY = null;

let smoothY = null;

const SMOOTHING = 0.25;

// ความไวในการเลื่อน
const SCROLL_SPEED = 16;

// ระยะที่ถือว่าเป็นการสั่น
const DEAD_ZONE = 0.003;


/* =========================================
   UTILITY
   ========================================= */

function distance(a, b) {

    return Math.sqrt(
        Math.pow(a.x - b.x, 2) +
        Math.pow(a.y - b.y, 2)
    );

}


function clamp(value, min, max) {

    return Math.max(
        min,
        Math.min(max, value)
    );

}


/* =========================================
   DETECT FINGERS
   ========================================= */

function getFingerState(lm) {

    return {

        index:
            lm[8].y < lm[6].y,

        middle:
            lm[12].y < lm[10].y,

        ring:
            lm[16].y < lm[14].y,

        pinky:
            lm[20].y < lm[18].y

    };

}


/* =========================================
   DETECT GESTURE
   ========================================= */

function detectGesture(lm) {

    const fingers =
        getFingerState(lm);


    const thumb =
        lm[4];

    const index =
        lm[8];


    const thumbIndex =
        distance(
            thumb,
            index
        );


    /*
      กางมือ

      ☝️ 🖐️
      นิ้วทั้งสี่ชู
    */

    const openHand =
        fingers.index &&
        fingers.middle &&
        fingers.ring &&
        fingers.pinky &&
        thumbIndex > 0.16;


    /*
      กำมือ

      ✊
    */

    const fist =
        !fingers.index &&
        !fingers.middle &&
        !fingers.ring &&
        !fingers.pinky;


    /*
      นิ้วชี้

      ☝️
    */

    const pointing =
        fingers.index &&
        !fingers.middle &&
        !fingers.ring &&
        !fingers.pinky;


    if (openHand)
        return "OPEN";


    if (fist)
        return "FIST";


    if (pointing)
        return "POINT";


    return "NONE";

}


/* =========================================
   TRACKPAD SCROLL
   ========================================= */

function trackpadScroll(lm) {

    const index =
        lm[8];


    /*
      index.y

      0 = ด้านบน
      1 = ด้านล่าง
    */


    if (smoothY === null) {

        smoothY =
            index.y;

    }


    /*
      Smooth ตำแหน่งนิ้ว
    */

    smoothY +=
        (index.y - smoothY)
        * SMOOTHING;


    if (previousIndexY === null) {

        previousIndexY =
            smoothY;

        return;

    }


    /*
      คำนวณการเคลื่อนที่
    */

    const movement =
        smoothY -
        previousIndexY;


    /*
      Dead Zone
      ป้องกันการสั่น
    */

    if (
        Math.abs(movement)
        < DEAD_ZONE
    ) {

        previousIndexY =
            smoothY;

        return;

    }


    /*
      นิ้วขึ้น
      → หน้าเว็บเลื่อนลง
    */

    if (movement < 0) {

        window.scrollBy({

            top:
                Math.abs(movement)
                * SCROLL_SPEED
                * 1000,

            behavior:
                "auto"

        });

    }


    /*
      นิ้วลง
      → หน้าเว็บเลื่อนขึ้น
    */

    else {

        window.scrollBy({

            top:
                -Math.abs(movement)
                * SCROLL_SPEED
                * 1000,

            behavior:
                "auto"

        });

    }


    previousIndexY =
        smoothY;

}


/* =========================================
   ZOOM
   ========================================= */

function updateZoom(gesture) {

    /*
      กางมือ
      → Zoom In
    */

    if (gesture === "OPEN") {

        zoom += 0.006;

    }


    /*
      กำมือ
      → Zoom Out
    */

    if (gesture === "FIST") {

        zoom -= 0.006;

    }


    zoom =
        clamp(
            zoom,
            MIN_ZOOM,
            MAX_ZOOM
        );


    website.style.transform =
        `scale(${zoom})`;


    zoomValue.textContent =
        Math.round(
            zoom * 100
        ) + "%";

}


/* =========================================
   DRAW HAND
   ========================================= */

function drawHand(lm) {

    ctx.clearRect(
        0,
        0,
        canvas.width,
        canvas.height
    );


    drawConnectors(
        ctx,
        lm,
        HAND_CONNECTIONS,
        {
            color:
                "#c59a4a",

            lineWidth:
                3
        }
    );


    drawLandmarks(
        ctx,
        lm,
        {
            color:
                "#f7efd9",

            radius:
                4
        }
    );

}


/* =========================================
   MEDIAPIPE RESULT
   ========================================= */

function onResults(results) {

    canvas.width =
        video.videoWidth ||
        640;

    canvas.height =
        video.videoHeight ||
        480;


    ctx.clearRect(
        0,
        0,
        canvas.width,
        canvas.height
    );


    /*
      ไม่มีมือ
    */

    if (
        !results.multiHandLandmarks ||
        results.multiHandLandmarks.length === 0
    ) {

        statusText.textContent =
            "ไม่พบมือ";

        cursor.style.display =
            "none";

        previousIndexY =
            null;

        smoothY =
            null;

        return;

    }


    const lm =
        results.multiHandLandmarks[0];


    drawHand(lm);


    const gesture =
        detectGesture(lm);


    /* =====================================
       ☝️ TRACKPAD
       ===================================== */

    if (
        gesture === "POINT"
    ) {

        const index =
            lm[8];


        /*
          เปลี่ยนตำแหน่งนิ้ว
          เป็น Cursor
        */

        const cursorX =
            (1 - index.x)
            * window.innerWidth;


        const cursorY =
            index.y
            * window.innerHeight;


        cursor.style.display =
            "block";


        cursor.style.left =
            cursorX + "px";


        cursor.style.top =
            cursorY + "px";


        /*
          เลื่อนหน้า
        */

        trackpadScroll(lm);


        statusText.textContent =
            "☝️ Trackpad — ขยับขึ้น/ลงเพื่อเลื่อน";


    }


    /* =====================================
       🖐️ ZOOM IN
       ===================================== */

    else if (
        gesture === "OPEN"
    ) {

        previousIndexY =
            null;

        smoothY =
            null;


        updateZoom(
            gesture
        );


        cursor.style.display =
            "none";


        statusText.textContent =
            "🖐️ กางมือ — กำลังขยาย";


    }


    /* =====================================
       ✊ ZOOM OUT
       ===================================== */

    else if (
        gesture === "FIST"
    ) {

        previousIndexY =
            null;

        smoothY =
            null;


        updateZoom(
            gesture
        );


        cursor.style.display =
            "none";


        statusText.textContent =
            "✊ หุบมือ — กำลังย่อ";


    }


    /* =====================================
       OTHER
       ===================================== */

    else {

        previousIndexY =
            null;

        smoothY =
            null;

        cursor.style.display =
            "none";


        statusText.textContent =
            "พร้อมใช้งาน";

    }

}


/* =========================================
   MEDIAPIPE
   ========================================= */

const hands =
    new Hands({

        locateFile:
            function(file) {

                return (
                    "https://cdn.jsdelivr.net/npm/@mediapipe/hands/"
                    + file
                );

            }

    });


hands.setOptions({

    maxNumHands:
        1,

    modelComplexity:
        1,

    minDetectionConfidence:
        0.65,

    minTrackingConfidence:
        0.65

});


hands.onResults(
    onResults
);


/* =========================================
   CAMERA
   ========================================= */

async function startCamera() {

    try {

        const stream =
            await navigator.mediaDevices
            .getUserMedia({

                video: {

                    width: 640,

                    height: 480,

                    facingMode:
                        "user"

                },

                audio:
                    false

            });


        video.srcObject =
            stream;


        await video.play();


        statusText.textContent =
            "กล้องพร้อมใช้งาน";


        /*
          เริ่มประมวลผล
        */

        async function processFrame() {

            if (
                video.readyState >= 2
            ) {

                await hands.send({

                    image:
                        video

                });

            }


            requestAnimationFrame(
                processFrame
            );

        }


        processFrame();

    }


    catch (error) {

        console.error(
            "Camera Error:",
            error
        );


        statusText.textContent =
            "ไม่สามารถเปิดกล้องได้";

    }

}


/* =========================================
   START
   ========================================= */

if (
    navigator.mediaDevices &&
    navigator.mediaDevices.getUserMedia
) {

    startCamera();

}

else {

    statusText.textContent =
        "Browser นี้ไม่รองรับ Camera";

}

</script>
