# Birth of Lord Rama 👑 — Complete HTML, CSS & JavaScript Game

I'll provide a playable, self-contained browser game based on your concept. It will use **HTML5 Canvas, CSS, and vanilla JavaScript**, with no external libraries or image assets required.

The implementation includes:

- **Five connected areas:** Palace Exterior, Royal Courtyard, Main Throne Hall, Queen's Chamber, and Celebration Courtyard.
- **32 × 18 conceptual tile grid:** Each tile represents one world unit.
- **Character movement:** Keyboard controls, collision detection, room boundaries, and door transitions.
- **Story interaction system:** Approach characters and objects to reveal dialogue and story details.
- **Characters:** King Dasharatha, Queen Kaushalya, baby Rama, the three infant princes, and palace attendants.
- **Opening cinematic:** A gentle celebration introducing the four princes.
- **Animations:** Breathing, moving attendants, fluttering flags, glowing lamps, and floating particles.
- **Audio:** Optional synthesized flute-like tones, bells, and ambient notes using the Web Audio API.
- **Progress tracking:** Complete the exploration objective, watch the birth celebration, and unlock Level 2.
- **Vector graphics:** Palace arches, pillars, lamps, lotus decorations, royal cradles, curtains, and ornaments drawn directly in Canvas.

The code below is designed to run without a server or build tools. I can't claim that it has been executed in a browser or independently test-validated here, so I've included runtime safeguards and a practical verification checklist rather than presenting unperformed tests as passed.

## 1\. Create the game file

Create a file named `index.html`, then copy the complete code below into it. Open the file in Chrome, Edge, Firefox, or another modern browser.

**Controls**

- `W`, `A`, `S`, `D` or arrow keys: Move.
- `E` or `Enter`: Interact with characters, objects, and doors.
- `Space`: Advance dialogue or the cinematic.
- `Esc`: Close a dialogue panel.
- `M`: Toggle audio.
- Touch controls: Available at the bottom of the game for mobile devices.

## 2\. Complete HTML, CSS and JavaScript

The following is one self-contained HTML file. It draws the game using vector shapes, so external graphics are not needed.

```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Birth of Lord Rama - Palace Adventure</title>

<style>
:root {
    --gold: #f6c85f;
    --saffron: #ed923b;
    --red: #8d2435;
    --cream: #fff1d1;
    --dark: #241322;
}

* {
    box-sizing: border-box;
}

body {
    margin: 0;
    min-height: 100vh;
    background:
        radial-gradient(ellipse at top, #69354a, #241322 75%);
    color: var(--cream);
    font-family: Georgia, "Times New Roman", serif;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 14px;
}

.game {
    width: min(1100px, 100%);
    border: 3px solid var(--gold);
    border-radius: 15px;
    overflow: hidden;
    background: #301a2a;
    box-shadow: 0 0 35px #0009;
}

header {
    padding: 13px 18px;
    background: linear-gradient(90deg, #6f2036, #a34736, #6f2036);
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 12px;
    flex-wrap: wrap;
    border-bottom: 2px solid var(--gold);
}

h1 {
    margin: 0;
    color: var(--gold);
    font-size: clamp(19px, 3vw, 28px);
}

.subtitle {
    margin-top: 5px;
    font-size: 12px;
    color: #ffe8bd;
}

button {
    font-family: inherit;
    cursor: pointer;
    color: #fff4d8;
    background: #772b3d;
    border: 1px solid var(--gold);
    border-radius: 7px;
    padding: 9px 13px;
    font-size: 14px;
}

button:hover {
    background: #a84742;
}

button:focus-visible {
    outline: 3px solid white;
    outline-offset: 2px;
}

.hud {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    gap: 8px;
    padding: 10px 15px;
    background: #281626;
    font-size: 13px;
}

.hud strong {
    color: var(--gold);
}

.canvas-wrap {
    position: relative;
    width: 100%;
    background: #3d2430;
}

canvas {
    display: block;
    width: 100%;
    height: auto;
    aspect-ratio: 16 / 9;
    image-rendering: auto;
    outline: none;
    touch-action: none;
}

.overlay {
    position: absolute;
    inset: 0;
    display: none;
    align-items: center;
    justify-content: center;
    padding: 16px;
    background: #160d1bd9;
    z-index: 2;
}

.overlay.visible {
    display: flex;
}

.panel {
    width: min(540px, 100%);
    max-height: 95%;
    overflow-y: auto;
    text-align: center;
    padding: 22px;
    border: 2px solid var(--gold);
    border-radius: 13px;
    background: linear-gradient(145deg, #773344, #351b32);
    box-shadow: 0 0 25px #0009;
}

.panel h2 {
    color: var(--gold);
    margin-top: 0;
}

.panel p {
    line-height: 1.65;
}

.panel .small {
    color: #f3d7bd;
    font-size: 13px;
}

.progress-track {
    height: 9px;
    background: #1c1020;
    border: 1px solid #b77c5b;
    border-radius: 20px;
    overflow: hidden;
    margin: 12px 0;
}

.progress-fill {
    height: 100%;
    width: 0%;
    background: linear-gradient(90deg, #ee913c, #ffe18a);
    transition: width 200ms;
}

footer {
    padding: 12px 15px;
    background: #281626;
    border-top: 1px solid #9b654d;
    font-size: 13px;
}

#objective {
    line-height: 1.6;
}

.controls {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 12px;
    margin-top: 12px;
}

.dpad {
    display: grid;
    grid-template-columns: repeat(3, 44px);
    grid-template-rows: repeat(2, 40px);
    gap: 4px;
}

.dpad button {
    padding: 4px;
    touch-action: none;
    user-select: none;
}

.dpad button:nth-child(1) {
    grid-column: 2;
}

.dpad button:nth-child(2) {
    grid-column: 1;
    grid-row: 2;
}

.dpad button:nth-child(3) {
    grid-column: 2;
    grid-row: 2;
}

.dpad button:nth-child(4) {
    grid-column: 3;
    grid-row: 2;
}

.action-controls {
    display: flex;
    gap: 7px;
    flex-wrap: wrap;
}

#toast {
    position: absolute;
    top: 12px;
    left: 50%;
    transform: translateX(-50%);
    background: #281626eF;
    color: #ffe6a5;
    border: 1px solid var(--gold);
    border-radius: 20px;
    padding: 8px 14px;
    font-size: 13px;
    text-align: center;
    max-width: 90%;
    pointer-events: none;
    opacity: 0;
    transition: opacity 180ms;
    z-index: 1;
}

#toast.visible {
    opacity: 1;
}

@media (max-width: 560px) {
    body {
        padding: 4px;
    }

    .game {
        border-width: 2px;
        border-radius: 8px;
    }

    header {
        padding: 10px;
    }

    .hud {
        font-size: 11px;
        padding: 8px;
    }

    footer {
        padding: 9px;
    }

    .panel {
        padding: 15px;
    }
}

@media (prefers-reduced-motion: reduce) {
    .progress-fill,
    #toast {
        transition: none;
    }
}
</style>
</head>

<body>
<main class="game">

<header>
    <div>
        <h1>👑 Birth of Lord Rama</h1>
        <div class="subtitle">An Ayodhya Palace Adventure · Level 1</div>
    </div>
    <button id="audioButton" type="button">♫ Audio: ON</button>
</header>

<section class="hud" aria-label="Game status">
    <span>📍 Room: <strong id="roomName">Palace Exterior</strong></span>
    <span>🧭 Tiles: <strong id="coordinates">3, 15</strong></span>
    <span>✨ Discoveries: <strong id="discoveryCount">0 / 5</strong></span>
    <span>🏆 Level: <strong id="levelStatus">1 — In Progress</strong></span>
</section>

<div class="canvas-wrap">
    <canvas
        id="gameCanvas"
        width="960"
        height="540"
        tabindex="0"
        role="img"
        aria-label="Two-dimensional palace adventure. Use the arrow keys to move, and E to interact."
    ></canvas>

    <div id="toast" role="status" aria-live="polite"></div>

    <div id="dialogOverlay" class="overlay" role="dialog"
         aria-modal="true" aria-labelledby="dialogTitle">
        <div class="panel">
            <h2 id="dialogTitle">A Royal Story</h2>
            <p id="dialogText"></p>
            <p class="small" id="dialogHint">Press E or Space to continue.</p>
            <button id="dialogButton" type="button">Continue ✨</button>
        </div>
    </div>

    <div id="cinematicOverlay" class="overlay" role="dialog"
         aria-modal="true" aria-labelledby="cinematicTitle">
        <div class="panel">
            <div style="font-size:44px" aria-hidden="true">🪷 👑 🪷</div>
            <h2 id="cinematicTitle">The Birth Celebration</h2>
            <p id="cinematicText"></p>
            <div class="progress-track" aria-label="Cinematic progress">
                <div class="progress-fill" id="cinematicProgress"></div>
            </div>
            <p class="small" id="cinematicHint">
                Press Space to continue the story.
            </p>
            <button id="cinematicButton" type="button">Continue</button>
        </div>
    </div>

    <div id="levelOverlay" class="overlay" role="dialog"
         aria-modal="true" aria-labelledby="levelTitle">
        <div class="panel">
            <div style="font-size:48px" aria-hidden="true">🏆 🪷 👑</div>
            <h2 id="levelTitle">Level 1 Complete!</h2>
            <p>
                The royal celebration has begun. You have explored the
                palace and witnessed the introduction of the four princes.
            </p>
            <p style="color:#ffe18a">
                LEVEL 2 UNLOCKED
            </p>
            <p class="small">
                This prototype unlocks Level 2; its gameplay is not yet implemented.
            </p>
            <button id="continueGameButton" type="button">Continue Exploring</button>
            <button id="restartButton" type="button">Restart Level 1</button>
        </div>
    </div>
</div>

<footer>
    <div id="objective">
        <strong>Objective:</strong> Explore the palace, discover five story
        objects, and visit the Queen's Chamber to witness the celebration.
    </div>

    <div class="progress-track">
        <div class="progress-fill" id="objectiveProgress"></div>
    </div>

    <div class="controls">
        <div>
            <strong>Movement</strong>
            <div class="small">WASD / Arrow keys · E Interact · Space Continue · M Audio</div>
        </div>

        <div class="dpad" aria-label="Touch movement controls">
            <button data-move="up" aria-label="Move up">▲</button>
            <button data-move="left" aria-label="Move left">◀</button>
            <button data-move="down" aria-label="Move down">▼</button>
            <button data-move="right" aria-label="Move right">▶</button>
        </div>

        <div class="action-controls">
            <button id="interactButton" type="button">Interact E</button>
            <button id="spaceButton" type="button">Continue</button>
        </div>
    </div>
</footer>

</main>

<script>
"use strict";

/* ==========================================================
   BIRTH OF LORD RAMA
   Canvas: 960 x 540
   Conceptual grid: 32 x 18 tiles
   Tile size: 30 x 30 pixels
   Dependencies: None
   ========================================================== */

(() => {
    const canvas = document.getElementById("gameCanvas");
    const ctx = canvas.getContext("2d");

    if (!ctx) {
        document.getElementById("objective").textContent =
            "Your browser does not support HTML Canvas. Please use a modern browser.";
        return;
    }

    const W = 960;
    const H = 540;
    const TILE = 30;
    const COLS = 32;
    const ROWS = 18;

    const $ = id => document.getElementById(id);

    const COLORS = {
        gold: "#f6c85f",
        goldDark: "#b77a30",
        saffron: "#e99742",
        cream: "#fff0ce",
        red: "#9e3041",
        darkRed: "#672536",
        wall: "#c97850",
        wallLight: "#f0bd7d",
        floor: "#e6b982",
        floorLight: "#f6d6a0",
        shadow: "rgba(36, 17, 28, 0.24)",
        green: "#527d52",
        sky: "#f4bc84"
    };

    const ROOM_NAMES = {
        exterior: "Palace Exterior",
        courtyard: "Royal Courtyard",
        throne: "Main Throne Hall",
        queen: "Queen's Chamber",
        celebration: "Celebration Courtyard"
    };

    const ROOM_ORDER = [
        "exterior",
        "courtyard",
        "throne",
        "queen",
        "celebration"
    ];

    const state = {
        room: "exterior",
        running: true,
        audioEnabled: true,
        audioContext: null,
        lastTime: 0,
        elapsed: 0,
        toastTimer: 0,
        cinematicTimer: 0,
        cinematicIndex: 0,
        cinematicStarted: false,
        cinematicFinished: false,
        levelUnlocked: false,
        dialogOpen: false,
        cinematicOpen: false,
        levelOpen: false,
        keys: new Set(),
        discoveries: new Set(),
        visitedRooms: new Set(["exterior"]),
        interactCooldown: 0,
        camera: { x: 0, y: 0 },
        particles: [],
        attendants: [],
        audioLastStep: 0
    };

    const player = {
        x: 3,
        y: 15,
        radius: 0.27,
        speed: 4.1,
        facing: "right",
        walkTime: 0
    };

    const doors = {
        exterior: [
            { x: 29, y: 8, to: "courtyard", spawnX: 2, spawnY: 8, label: "Royal Gateway" }
        ],
        courtyard: [
            { x: 2, y: 8, to: "exterior", spawnX: 29, spawnY: 8, label: "Palace Gate" },
            { x: 29, y: 8, to: "throne", spawnX: 2, spawnY: 8, label: "Throne Hall" }
        ],
        throne: [
            { x: 2, y: 8, to: "courtyard", spawnX: 29, spawnY: 8, label: "Courtyard Arch" },
            { x: 29, y: 8, to: "queen", spawnX: 2, spawnY: 8, label: "Queen's Chamber" }
        ],
        queen: [
            { x: 2, y: 8, to: "throne", spawnX: 29, spawnY: 8, label: "Throne Hall" },
            { x: 29, y: 8, to: "celebration", spawnX: 2, spawnY: 8, label: "Celebration Courtyard" }
        ],
        celebration: [
            { x: 2, y: 8, to: "queen", spawnX: 29, spawnY: 8, label: "Queen's Chamber" }
        ]
    };

    /*
     * Objects are positioned in grid units.
     * Each object provides a stable ID, display name and story.
     */
    const objects = [
        {
            id: "royal_banner",
            room: "exterior",
            x: 12, y: 5,
            name: "Royal Banner",
            title: "The Royal Banner",
            text: "The flags of Ayodhya flutter above the palace. King Dasharatha's kingdom is preparing for a momentous event.",
            kind: "banner"
        },
        {
            id: "lotus_fountain",
            room: "courtyard",
            x: 15, y: 10,
            name: "Lotus Fountain",
            title: "The Sacred Lotus",
            text: "Lotuses bloom in the royal courtyard. The flowers symbolize purity, hope, and auspicious beginnings.",
            kind: "lotus"
        },
        {
            id: "royal_throne",
            room: "throne",
            x: 16, y: 7,
            name: "Royal Throne",
            title: "The Throne of Ayodhya",
            text: "King Dasharatha rules Ayodhya from this magnificent throne. The palace awaits news that will bring joy to the kingdom.",
            kind: "throne"
        },
        {
            id: "royal_lamp",
            room: "throne",
            x: 22, y: 12,
            name: "Golden Lamp",
            title: "The Auspicious Lamp",
            text: "A golden lamp glows softly in the palace hall. Its light represents hope, warmth, and the beginning of a blessed chapter.",
            kind: "lamp"
        },
        {
            id: "royal_cradle",
            room: "queen",
            x: 17, y: 9,
            name: "Royal Cradle",
            title: "The Birth of Lord Rama",
            text: "In Queen Kaushalya's chamber, baby Rama rests in a beautifully decorated cradle. The palace prepares to celebrate the birth of the beloved prince.",
            kind: "cradle"
        },
        {
            id: "queen_lotus",
            room: "queen",
            x: 23, y: 5,
            name: "Lotus Ornament",
            title: "A Lotus Ornament",
            text: "Delicate lotus motifs adorn the Queen's Chamber, adding to the peaceful and auspicious atmosphere.",
            kind: "ornament"
        },
        {
            id: "celebration_lamps",
            room: "celebration",
            x: 17, y: 6,
            name: "Festival Lamps",
            title: "The Festival of Joy",
            text: "Golden lamps illuminate the celebration courtyard. Attendants prepare flowers and decorations for the royal family.",
            kind: "festival"
        }
    ];

    const characters = [
        {
            id: "dasharatha",
            room: "throne",
            x: 12,
            y: 9,
            name: "King Dasharatha",
            color: "#8b3042",
            title: "King Dasharatha",
            text: "Welcome to Ayodhya, young explorer! The palace is filled with hope and happiness. Please explore the royal halls and visit the Queen's Chamber."
        },
        {
            id: "attendant1",
            room: "courtyard",
            x: 12,
            y: 8,
            name: "Palace Attendant",
            color: "#bd653e",
            title: "Palace Attendant",
            text: "The palace is being decorated with flowers and lamps. A wonderful celebration is about to begin!"
        },
        {
            id: "attendant2",
            room: "queen",
            x: 23,
            y: 10,
            name: "Royal Attendant",
            color: "#557c73",
            title: "Royal Attendant",
            text: "Queen Kaushalya is in her chamber. Please approach the royal cradle to learn about the birth of Prince Rama."
        },
        {
            id: "kaushalya",
            room: "queen",
            x: 12,
            y: 9,
            name: "Queen Kaushalya",
            color: "#426c99",
            title: "Queen Kaushalya",
            text: "May peace and happiness fill Ayodhya. My beloved son Rama brings great joy to our family and kingdom."
        },
        {
            id: "celebrant",
            room: "celebration",
            x: 12,
            y: 10,
            name: "Palace Attendant",
            color: "#a04455",
            title: "The Royal Celebration",
            text: "Flowers, lamps, and music fill the courtyard! The whole palace celebrates the arrival of the four princes."
        }
    ];

    const cinematicScenes = [
        {
            title: "A Joyful Day in Ayodhya",
            text: "The royal palace shines beneath the warm light of a new day. King Dasharatha and the people of Ayodhya await a moment of extraordinary happiness."
        },
        {
            title: "The Birth of Prince Rama",
            text: "Queen Kaushalya welcomes her beloved son, Rama. His birth fills the royal family with joy, hope, and devotion."
        },
        {
            title: "Four Royal Princes",
            text: "The palace celebrates four princes: Rama, Bharata, Lakshmana, and Shatrughna. The attendants prepare lamps, flowers, and music for the joyful occasion."
        },
        {
            title: "A New Chapter Begins",
            text: "The birth celebration marks the beginning of Rama's great story. Ayodhya rejoices as the royal family looks forward to the princes' future."
        }
    ];

    function clamp(value, min, max) {
        return Math.max(min, Math.min(max, value));
    }

    function distance(a, b) {
        return Math.hypot(a.x - b.x, a.y - b.y);
    }

    function roundRect(x, y, w, h, r, fill, stroke) {
        ctx.beginPath();
        ctx.roundRect(x, y, w, h, r);

        if (fill) {
            ctx.fillStyle = fill;
            ctx.fill();
        }

        if (stroke) {
            ctx.strokeStyle = stroke;
            ctx.lineWidth = 2;
            ctx.stroke();
        }
    }

    function ellipse(x, y, rx, ry, fill, stroke) {
        ctx.beginPath();
        ctx.ellipse(x, y, rx, ry, 0, 0, Math.PI * 2);
        ctx.fillStyle = fill;
        ctx.fill();

        if (stroke) {
            ctx.strokeStyle = stroke;
            ctx.lineWidth = 1.5;
            ctx.stroke();
        }
    }

    function line(x1, y1, x2, y2, color, width = 2) {
        ctx.beginPath();
        ctx.moveTo(x1, y1);
        ctx.lineTo(x2, y2);
        ctx.strokeStyle = color;
        ctx.lineWidth = width;
        ctx.stroke();
    }

    function polygon(points, fill, stroke) {
        if (!points.length) return;

        ctx.beginPath();
        ctx.moveTo(points[0][0], points[0][1]);

        for (let i = 1; i < points.length; i++) {
            ctx.lineTo(points[i][0], points[i][1]);
        }

        ctx.closePath();
        ctx.fillStyle = fill;
        ctx.fill();

        if (stroke) {
            ctx.strokeStyle = stroke;
            ctx.lineWidth = 2;
            ctx.stroke();
        }
    }

    function text(str, x, y, size, color, align = "center") {
        ctx.save();
        ctx.font = `bold ${size}px Georgia, serif`;
        ctx.textAlign = align;
        ctx.textBaseline = "middle";
        ctx.fillStyle = color;
        ctx.fillText(str, x, y);
        ctx.restore();
    }

    /* ---------------- AUDIO ---------------- */

    function initAudio() {
        if (!state.audioEnabled) return;

        try {
            if (!state.audioContext) {
                const AudioCtor =
                    window.AudioContext || window.webkitAudioContext;

                if (!AudioCtor) {
                    state.audioEnabled = false;
                    updateAudioButton();
                    showToast("Web Audio is not supported in this browser.");
                    return;
                }

                state.audioContext = new AudioCtor();
            }

            if (state.audioContext.state === "suspended") {
                state.audioContext.resume().catch(() => {});
            }
        } catch (error) {
            state.audioEnabled = false;
            updateAudioButton();
        }
    }

    function tone(frequency, duration = 0.25, volume = 0.035, type = "sine") {
        if (!state.audioEnabled) return;

        initAudio();

        const ac = state.audioContext;
        if (!ac || ac.state !== "running") return;

        try {
            const oscillator = ac.createOscillator();
            const gain = ac.createGain();

            oscillator.type = type;
            oscillator.frequency.setValueAtTime(frequency, ac.currentTime);

            gain.gain.setValueAtTime(Math.max(0.0001, volume), ac.currentTime);
            gain.gain.exponentialRampToValueAtTime(
                0.0001,
                ac.currentTime + duration
            );

            oscillator.connect(gain);
            gain.connect(ac.destination);

            oscillator.start();
            oscillator.stop(ac.currentTime + duration);
        } catch (error) {
            // Audio is optional; a sound failure must not stop gameplay.
        }
    }

    function playBell() {
        tone(880, 0.65, 0.035, "sine");
        window.setTimeout(() => tone(1175, 0.5, 0.02, "sine"), 100);
    }

    function playFootstep() {
        tone(120, 0.07, 0.008, "triangle");
    }

    function updateAudioButton() {
        $("audioButton").textContent =
            state.audioEnabled ? "♫ Audio: ON" : "♫ Audio: OFF";
    }

    $("audioButton").addEventListener("click", () => {
        state.audioEnabled = !state.audioEnabled;

        if (state.audioEnabled) {
            initAudio();
            tone(523.25, 0.18, 0.025);
        }

        updateAudioButton();
    });

    /* ---------------- USER INTERFACE ---------------- */

    function showToast(message) {
        const el = $("toast");
        el.textContent = message;
        el.classList.add("visible");

        state.toastTimer = 2.3;
    }

    function openDialog(title, message) {
        state.dialogOpen = true;

        $("dialogTitle").textContent = title;
        $("dialogText").textContent = message;
        $("dialogOverlay").classList.add("visible");

        $("dialogButton").focus();
        playBell();
    }

    function closeDialog() {
        state.dialogOpen = false;
        $("dialogOverlay").classList.remove("visible");
        canvas.focus();
    }

    $("dialogButton").addEventListener("click", closeDialog);

    $("continueGameButton").addEventListener("click", () => {
        state.levelOpen = false;
        $("levelOverlay").classList.remove("visible");
        canvas.focus();
    });

    $("restartButton").addEventListener("click", restartGame);

    function updateHUD() {
        $("roomName").textContent = ROOM_NAMES[state.room];
        $("coordinates").textContent =
            `${Math.floor(player.x)}, ${Math.floor(player.y)}`;

        $("discoveryCount").textContent =
            `${state.discoveries.size} / 5`;

        $("levelStatus").textContent = state.levelUnlocked
            ? "2 — Unlocked"
            : "1 — In Progress";

        const discoveryProgress =
            Math.min(100, state.discoveries.size / 5 * 100);

        $("objectiveProgress").style.width = discoveryProgress + "%";

        let objective = "";

        if (!state.discoveries.has("royal_banner")) {
            objective = "Discover the Royal Banner outside the palace.";
        } else if (!state.discoveries.has("lotus_fountain")) {
            objective = "Explore the Royal Courtyard and inspect the lotus fountain.";
        } else if (!state.discoveries.has("royal_throne")) {
            objective = "Enter the Main Throne Hall and inspect the royal throne.";
        } else if (!state.discoveries.has("royal_cradle")) {
            objective = "Visit the Queen's Chamber and interact with the royal cradle.";
        } else if (!state.cinematicFinished) {
            objective = "Watch the opening celebration cinematic.";
        } else {
            objective = "Level 1 complete! Level 2 is unlocked.";
        }

        $("objective").innerHTML = "<strong>Objective:</strong> " + objective;
    }

    /* ---------------- WORLD AND COLLISIONS ---------------- */

    function roomDoors() {
        return doors[state.room] || [];
    }

    function activeObjects() {
        return objects.filter(obj => obj.room === state.room);
    }

    function activeCharacters() {
        return characters.filter(char => char.room === state.room);
    }

    function blockedAt(x, y) {
        // Keep the player within the 32 x 18 conceptual grid.
        if (x < 0.55 || x > COLS - 0.55 ||
            y < 0.65 || y > ROWS - 0.65) {
            return true;
        }

        // Decorative pillars act as solid obstacles.
        const pillars = [
            { x: 5, y: 5 },
            { x: 5, y: 12 },
            { x: 26, y: 5 },
            { x: 26, y: 12 }
        ];

        if (state.room === "exterior" || state.room === "celebration") {
            // Exterior and celebration paths remain relatively open.
        } else {
            for (const p of pillars) {
                if (Math.abs(x - p.x) < 0.52 &&
                    Math.abs(y - p.y) < 0.52) {
                    return true;
                }
            }
        }

        // Furniture collision in the throne hall.
        if (state.room === "throne") {
            if (Math.abs(x - 16) < 1.1 && Math.abs(y - 7) < 0.65) {
                return true;
            }
        }

        // Cradle collision in the Queen's Chamber.
        if (state.room === "queen") {
            if (Math.abs(x - 17) < 1.05 && Math.abs(y - 9) < 0.6) {
                return true;
            }
        }

        return false;
    }

    function movePlayer(dx, dy, dt) {
        const moving = Math.abs(dx) + Math.abs(dy) > 0;

        if (!moving || state.dialogOpen || state.cinematicOpen ||
            state.levelOpen) {
            return;
        }

        // Normalize diagonal movement to prevent faster diagonal travel.
        const length = Math.hypot(dx, dy) || 1;
        dx /= length;
        dy /= length;

        const step = player.speed * dt;

        if (dx < 0) player.facing = "left";
        if (dx > 0) player.facing = "right";

        // Axis-separated collision resolution.
        const nx = player.x + dx * step;
        const ny = player.y + dy * step;

        if (!blockedAt(nx, player.y)) {
            player.x = nx;
        }

        if (!blockedAt(player.x, ny)) {
            player.y = ny;
        }

        player.walkTime += dt * 9;

        if (state.elapsed - state.audioLastStep > 0.35) {
            playFootstep();
            state.audioLastStep = state.elapsed;
        }
    }

    function transitionRoom(door) {
        state.room = door.to;
        player.x = door.spawnX;
        player.y = door.spawnY;

        state.visitedRooms.add(door.to);
        state.camera.x = 0;
        state.camera.y = 0;

        state.keys.clear();

        playBell();

        showToast("Entered: " + ROOM_NAMES[door.to]);
        updateHUD();
    }

    /* ---------------- INTERACTION SYSTEM ---------------- */

    function nearestInteraction() {
        let nearest = null;
        let nearestDistance = Infinity;

        for (const obj of activeObjects()) {
            const d = distance(player, obj);

            if (d < 1.55 && d < nearestDistance) {
                nearest = { type: "object", data: obj, distance: d };
                nearestDistance = d;
            }
        }

        for (const char of activeCharacters()) {
            const d = distance(player, char);

            if (d < 1.6 && d < nearestDistance) {
                nearest = { type: "character", data: char, distance: d };
                nearestDistance = d;
            }
        }

        for (const door of roomDoors()) {
            const d = distance(player, door);

            if (d < 1.5 && d < nearestDistance) {
                nearest = { type: "door", data: door, distance: d };
                nearestDistance = d;
            }
        }

        return nearest;
    }

    function interact() {
        if (state.dialogOpen) {
            closeDialog();
            return;
        }

        if (state.cinematicOpen) {
            nextCinematicScene();
            return;
        }

        if (state.levelOpen) return;

        initAudio();

        const target = nearestInteraction();

        if (!target) {
            showToast("Explore nearby objects, characters, and doors.");
            return;
        }

        if (target.type === "door") {
            transitionRoom(target.data);
            return;
        }

        if (target.type === "character") {
            const char = target.data;

            if (char.id === "dasharatha") {
                state.discoveries.add("dasharatha_met");
            }

            if (char.id === "kaushalya") {
                state.discoveries.add("kaushalya_met");
            }

            openDialog(char.title, char.text);
            updateHUD();
            return;
        }

        if (target.type === "object") {
            const obj = target.data;

            if (!state.discoveries.has(obj.id)) {
                state.discoveries.add(obj.id);
                playBell();
            }

            openDialog(obj.title, obj.text);

            if (obj.id === "royal_cradle" && !state.cinematicFinished) {
                $("dialogText").textContent =
                    obj.text + " The opening celebration is ready to begin.";

                $("dialogHint").textContent =
                    "Close this message, then interact with the cradle again to begin the cinematic.";
            }

            updateHUD();
        }
    }

    /*
     * The cinematic is triggered by interacting with the cradle
     * for the second time after its story has been discovered.
     *
     * This gives players a chance to read the cradle's description.
     */
    function interactWithCradle() {
        const cradle = objects.find(o => o.id === "royal_cradle");

        if (!cradle || state.room !== "queen") return false;

        if (distance(player, cradle) >= 1.55) return false;

        if (state.dialogOpen || state.cinematicOpen || state.levelOpen) {
            return false;
        }

        if (!state.discoveries.has("royal_cradle")) {
            return false;
        }

        startCinematic();
        return true;
    }

    const originalInteract = interact;

    function safeInteract() {
        if (state.dialogOpen) {
            closeDialog();
            return;
        }

        if (state.cinematicOpen) {
            nextCinematicScene();
            return;
        }

        if (state.levelOpen) return;

        if (interactWithCradle()) return;

        originalInteract();
    }

    /* ---------------- CINEMATIC ---------------- */

    function startCinematic() {
        if (state.cinematicFinished || state.cinematicOpen) return;

        state.cinematicOpen = true;
        state.cinematicStarted = true;
        state.cinematicIndex = 0;
        state.cinematicTimer = 0;

        state.keys.clear();

        $("cinematicOverlay").classList.add("visible");

        updateCinematic();
        playBell();
    }

    function updateCinematic() {
        const scene = cinematicScenes[state.cinematicIndex];

        if (!scene) return;

        $("cinematicTitle").textContent = scene.title;
        $("cinematicText").textContent = scene.text;

        $("cinematicProgress").style.width =
            ((state.cinematicIndex + 1) / cinematicScenes.length * 100) + "%";

        const last = state.cinematicIndex === cinematicScenes.length - 1;

        $("cinematicButton").textContent =
            last ? "Complete Celebration ✨" : "Next Scene →";

        $("cinematicHint").textContent =
            last
                ? "Finish the celebration to unlock Level 2."
                : "Press Space or click Next Scene to continue.";

        tone([523.25, 587.33, 659.25, 783.99][state.cinematicIndex],
            0.55, 0.025);
    }

    function nextCinematicScene() {
        if (!state.cinematicOpen) return;

        state.cinematicIndex++;

        if (state.cinematicIndex >= cinematicScenes.length) {
            finishCinematic();
            return;
        }

        updateCinematic();
    }

    function finishCinematic() {
        state.cinematicOpen = false;
        state.cinematicFinished = true;
        state.levelUnlocked = true;

        $("cinematicOverlay").classList.remove("visible");
        $("levelOverlay").classList.add("visible");

        state.levelOpen = true;

        playBell();
        updateHUD();
    }

    $("cinematicButton").addEventListener("click", nextCinematicScene);

    /* ---------------- VECTOR ART ---------------- */

    function drawSky() {
        const gradient = ctx.createLinearGradient(0, 0, 0, H);
        gradient.addColorStop(0, "#f4b77c");
        gradient.addColorStop(0.55, "#f8d7a1");
        gradient.addColorStop(1, "#e9b67e");

        ctx.fillStyle = gradient;
        ctx.fillRect(0, 0, W, H);

        // Sun.
        ellipse(815, 85, 39, 39, "#ffedb0");
        ellipse(815, 85, 29, 29, "#ffe5a0");

        // Distant hills.
        polygon([
            [0, 220], [130, 155], [250, 218],
            [390, 140], [550, 220], [710, 165],
            [850, 215], [960, 150], [960, 330], [0, 330]
        ], "#d99a77");

        polygon([
            [0, 265], [190, 205], [350, 270],
            [550, 200], [735, 275], [960, 210],
            [960, 400], [0, 400]
        ], "#bd846a");
    }

    function drawFloor() {
        ctx.fillStyle = COLORS.floor;
        ctx.fillRect(0, 0, W, H);

        for (let row = 0; row < ROWS; row++) {
            for (let col = 0; col < COLS; col++) {
                const x = col * TILE;
                const y = row * TILE;

                ctx.fillStyle =
                    (row + col) % 2 === 0
                        ? COLORS.floorLight
                        : COLORS.floor;

                ctx.fillRect(x, y, TILE, TILE);

                ctx.strokeStyle = "#a9684530";
                ctx.lineWidth = 1;
                ctx.strokeRect(x, y, TILE, TILE);
            }
        }

        // Royal decorative floor border.
        ctx.strokeStyle = COLORS.goldDark;
        ctx.lineWidth = 7;
        ctx.strokeRect(10, 10, W - 20, H - 20);

        ctx.strokeStyle = COLORS.cream;
        ctx.lineWidth = 2;
        ctx.strokeRect(18, 18, W - 36, H - 36);
    }

    function drawArch(x, y, w, h) {
        ctx.fillStyle = COLORS.darkRed;
        ctx.fillRect(x, y + h * 0.38, w, h * 0.62);

        ctx.beginPath();
        ctx.moveTo(x, y + h * 0.42);
        ctx.lineTo(x, y + h * 0.22);
        ctx.quadraticCurveTo(x + w / 2, y - h * 0.25, x + w, y + h * 0.22);
        ctx.lineTo(x + w, y + h * 0.42);
        ctx.closePath();

        ctx.fillStyle = COLORS.wallLight;
        ctx.fill();
        ctx.strokeStyle = COLORS.goldDark;
        ctx.lineWidth = 5;
        ctx.stroke();

        ctx.fillStyle = COLORS.darkRed;
        ctx.fillRect(x + 13, y + h * 0.38, w - 26, h * 0.62);

        // Decorative arch rosettes.
        ellipse(x + w / 2, y + h * 0.05, 8, 8, COLORS.gold);
    }

    function drawPillar(x, y, scale = 1) {
        ctx.save();
        ctx.translate(x, y);
        ctx.scale(scale, scale);

        ctx.fillStyle = COLORS.goldDark;
        ctx.fillRect(-12, -45, 24, 78);

        ctx.fillStyle = COLORS.cream;
        ctx.fillRect(-9, -43, 18, 73);

        ctx.fillStyle = COLORS.saffron;
        ctx.fillRect(-12, -48, 24, 9);
        ctx.fillRect(-15, 29, 30, 8);

        for (let yy = -30; yy <= 15; yy += 15) {
            line(-7, yy, 7, yy, COLORS.goldDark, 2);
        }

        polygon([
            [-16, -48], [-11, -57], [11, -57], [16, -48]
        ], COLORS.gold, COLORS.goldDark);

        ellipse(0, -62, 7, 7, COLORS.red, COLORS.gold);

        ctx.restore();
    }

    function drawLamp(x, y, scale = 1) {
        ctx.save();
        ctx.translate(x, y);
        ctx.scale(scale, scale);

        line(0, -25, 0, -4, COLORS.goldDark, 3);

        polygon([
            [-14, -7], [-10, 0], [10, 0], [14, -7]
        ], COLORS.gold, COLORS.goldDark);

        ellipse(0, -10, 5, 10, "#ffefad");

        const glow = ctx.createRadialGradient(0, -12, 2, 0, -12, 29);
        glow.addColorStop(0, "#ffdc7c88");
        glow.addColorStop(1, "#ffdc7c00");

        ctx.fillStyle = glow;
        ctx.fillRect(-30, -42, 60, 60);

        ctx.restore();
    }

    function drawLotus(x, y, scale = 1) {
        ctx.save();
        ctx.translate(x, y);
        ctx.scale(scale, scale);

        const colors = ["#e88d9b", "#f4bac1", "#d96d87"];

        for (let i = 0; i < 8; i++) {
            const a = i * Math.PI / 4;

            ctx.save();
            ctx.translate(Math.cos(a) * 8, Math.sin(a) * 8);
            ctx.rotate(a);
            ellipse(0, -9, 6, 12, colors[i % colors.length], "#a84b62");
            ctx.restore();
        }

        ellipse(0, 0, 7, 7, COLORS.gold, "#a84b62");
        ctx.restore();
    }

    function drawCurtain(x, y, w, h) {
        ctx.fillStyle = COLORS.red;
        ctx.fillRect(x, y, w, h);

        for (let i = 0; i < w; i += 14) {
            polygon([
                [x + i, y],
                [x + i + 7, y + h],
                [x + i + 14, y + h],
                [x + i + 7, y]
            ], "#bd4a4d");
        }

        ctx.fillStyle = COLORS.gold;
        ctx.fillRect(x, y + h - 7, w, 7);

        for (let i = 8; i < w; i += 22) {
            drawLotus(x + i, y + h - 12, 0.35);
        }
    }

    function drawCradle(x, y) {
        const bob = Math.sin(state.elapsed * 2.3) * 1.8;

        ctx.save();
        ctx.translate(x, y + bob);

        // Cradle supports.
        line(-37, 10, -28, 37, COLORS.goldDark, 5);
        line(37, 10, 28, 37, COLORS.goldDark, 5);

        // Rocking cradle.
        ctx.fillStyle = "#a94a3b";
        ctx.beginPath();
        ctx.moveTo(-39, -2);
        ctx.quadraticCurveTo(0, 35, 39, -2);
        ctx.lineTo(32, 13);
        ctx.quadraticCurveTo(0, 42, -32, 13);
        ctx.closePath();
        ctx.fill();

        ctx.strokeStyle = COLORS.gold;
        ctx.lineWidth = 4;
        ctx.stroke();

        // Baby Rama.
        ellipse(0, -8, 23, 13, "#f2c69c");
        ellipse(-5, -15, 12, 11, "#a7c5d4");
        ellipse(-8, -17, 2, 2, "#472334");
        ellipse(-1, -17, 2, 2, "#472334");

        // Blanket.
        polygon([
            [-24, -2], [25, -2], [19, 9], [-19, 9]
        ], "#537da0", COLORS.gold);

        // Royal head ornament.
        polygon([
            [-10, -25], [-5, -34], [0, -27],
            [6, -35], [12, -25]
        ], COLORS.gold, COLORS.goldDark);

        // Crown jewel.
        ellipse(0, -29, 3, 3, COLORS.red);

        ctx.restore();
    }

    function drawThrone(x, y) {
        ctx.save();
        ctx.translate(x, y);

        roundRect(-42, -46, 84, 78, 13, COLORS.red, COLORS.gold);
        roundRect(-31, -35, 62, 62, 8, "#b9633e", COLORS.goldDark);

        polygon([
            [-36, -44], [-24, -64], [-12, -45],
            [0, -69], [12, -45], [24, -64], [36, -44]
        ], COLORS.gold, COLORS.goldDark);

        ellipse(0, -59, 5, 5, "#e95d6b", COLORS.gold);

        ctx.fillStyle = COLORS.gold;
        ctx.fillRect(-43, 24, 86, 8);

        ctx.restore();
    }

    function drawBanner(x, y, time) {
        line(x, y, x, y + 80, COLORS.goldDark, 5);

        const wave = Math.sin(time * 3) * 5;

        polygon([
            [x, y + 5],
            [x + 52, y + 14 + wave],
            [x + 45, y + 35],
            [x, y + 29]
        ], COLORS.red, COLORS.gold);

        drawLotus(x + 22, y + 22 + wave / 2, 0.45);
    }

    function drawRoomArchitecture() {
        switch (state.room) {
            case "exterior":
                drawSky();

                // Palace silhouette.
                ctx.fillStyle = "#a8493e";
                ctx.fillRect(170, 125, 620, 230);

                for (let i = 0; i < 5; i++) {
                    drawArch(185 + i * 120, 175, 100, 160);
                }

                // Central royal dome.
                ellipse(480, 130, 100, 55, COLORS.saffron, COLORS.goldDark);
                ctx.fillStyle = COLORS.red;
                ctx.fillRect(390, 130, 180, 45);

                polygon([
                    [395, 135], [425, 75], [480, 43],
                    [535, 75], [565, 135]
                ], COLORS.saffron, COLORS.goldDark);

                line(480, 42, 480, 16, COLORS.gold, 4);
                ellipse(480, 15, 5, 5, COLORS.gold);

                drawBanner(250, 85, state.elapsed);
                drawBanner(700, 85, state.elapsed + 1.2);

                // Open approach.
                ctx.fillStyle = "#d6a16d";
                ctx.fillRect(365, 355, 230, 185);

                text("AYODHYA", 480, 387, 18, COLORS.cream);
                break;

            case "courtyard":
                drawFloor();

                // Garden beds.
                roundRect(80, 100, 200, 95, 15, "#648257", COLORS.goldDark);
                roundRect(680, 100, 200, 95, 15, "#648257", COLORS.goldDark);

                for (let i = 0; i < 6; i++) {
                    drawLotus(105 + i * 30, 145 + Math.sin(i) * 10, 0.55);
                    drawLotus(705 + i * 30, 145 + Math.cos(i) * 10, 0.55);
                }

                drawArch(380, 45, 200, 175);
                drawPillar(115, 250);
                drawPillar(845, 250);

                ellipse(480, 330, 110, 46, "#b2d8d1", COLORS.goldDark);
                ellipse(480, 330, 82, 31, "#73aaa7", "#f6e0ac");
                drawLotus(480, 321, 0.9);

                drawBanner(320, 80, state.elapsed);
                drawBanner(640, 80, state.elapsed + 0.7);
                break;

            case "throne":
                drawFloor();

                ctx.fillStyle = "#b25b46";
                ctx.fillRect(0, 0, W, 92);

                drawCurtain(35, 0, 170, 115);
                drawCurtain(755, 0, 170, 115);

                drawArch(360, 10, 240, 185);

                drawPillar(95, 220, 1.2);
                drawPillar(865, 220, 1.2);
                drawPillar(95, 430, 1.0);
                drawPillar(865, 430, 1.0);

                drawThrone(480, 255);

                drawLamp(285, 330, 0.9);
                drawLamp(675, 330, 0.9);

                for (let i = 0; i < 5; i++) {
                    drawLotus(385 + i * 48, 65, 0.4);
                }
                break;

            case "queen":
                drawFloor();

                ctx.fillStyle = "#a65b57";
                ctx.fillRect(0, 0, W, 80);

                drawCurtain(45, 0, 205, 135);
                drawCurtain(710, 0, 205, 135);

                drawArch(345, 18, 270, 195);

                drawPillar(90, 220, 1.0);
                drawPillar(870, 220, 1.0);

                // Rug beneath the royal cradle.
                roundRect(360, 275, 255, 155, 20, "#b24c50", COLORS.gold);
                ctx.strokeStyle = "#f7d38d";
                ctx.lineWidth = 3;
                ctx.strokeRect(377, 292, 221, 121);

                for (let i = 0; i < 4; i++) {
                    drawLotus(395 + i * 60, 305, 0.4);
                    drawLotus(395 + i * 60, 400, 0.4);
                }

                drawLamp(290, 355, 0.85);
                drawLamp(685, 355, 0.85);
                drawLotus(480, 135, 1.1);
                drawCradle(510, 335);
                break;

            case "celebration":
                drawFloor();

                ctx.fillStyle = "#a95143";
                ctx.fillRect(0, 0, W, 105);

                drawCurtain(20, 0, 210, 100);
                drawCurtain(730, 0, 210, 100);

                drawArch(370, 15, 220, 180);

                for (let i = 0; i < 7; i++) {
                    drawLamp(120 + i * 120, 165 + Math.sin(i) * 10, 0.7);
                }

                // Celebration decorations.
                for (let i = 0; i < 12; i++) {
                    drawLotus(100 + i * 68, 285 + Math.sin(i * 1.7) * 32, 0.45);
                }

                drawBanner(285, 75, state.elapsed);
                drawBanner(675, 75, state.elapsed + 1.3);

                drawThrone(480, 365);
                break;
        }
    }

    function drawObject(obj) {
        const x = obj.x * TILE + TILE / 2;
        const y = obj.y * TILE + TILE / 2;

        switch (obj.kind) {
            case "banner":
                drawBanner(x, y - 35, state.elapsed);
                break;

            case "lotus":
                ellipse(x, y, 43, 24, "#79aaa0", COLORS.gold);
                drawLotus(x, y, 1.4);
                break;

            case "throne":
                drawThrone(x, y);
                break;

            case "lamp":
                drawLamp(x, y, 1);
                break;

            case "cradle":
                drawCradle(x, y);
                break;

            case "ornament":
                drawLotus(x, y, 1.4);
                break;

            case "festival":
                drawLamp(x, y, 1.1);
                drawLotus(x + 35, y + 6, 0.65);
                break;
        }

        if (nearestInteraction()?.data?.id === obj.id) {
            drawInteractionMarker(x, y - 43);
        }
    }

    function drawInteractionMarker(x, y) {
        const bob = Math.sin(state.elapsed * 5) * 4;

        ellipse(x, y + bob, 13, 13, COLORS.gold, "#7c3a36");
        text("E", x, y + bob + 1, 13, "#52232e");
    }

    function drawCharacter(char) {
        const x = char.x * TILE + TILE / 2;
        const y = char.y * TILE + TILE / 2;
        const bob = Math.sin(state.elapsed * 2.5 + char.x) * 1.2;

        ctx.save();
        ctx.translate(x, y + bob);

        // Ground shadow.
        ellipse(0, 12, 14, 5, COLORS.shadow);

        // Body and robe.
        polygon([
            [-12, -5], [-10, -17], [10, -17],
            [12, -5], [15, 12], [-15, 12]
        ], char.color, COLORS.goldDark);

        // Head.
        ellipse(0, -23, 10, 11, "#e9b68c", "#9a624e");

        // Hair.
        ellipse(0, -29, 10, 6, "#4b2931");

        // Crown / hair ornament for the king and queen.
        if (char.id === "dasharatha" || char.id === "kaushalya") {
            polygon([
                [-9, -30], [-6, -39], [0, -34],
                [6, -39], [9, -30]
            ], COLORS.gold, COLORS.goldDark);

            ellipse(0, -35, 3, 3, COLORS.red);
        }

        // Eyes.
        ellipse(-3, -23, 1.4, 1.5, "#33202a");
        ellipse(3, -23, 1.4, 1.5, "#33202a");

        // Belt.
        line(-9, 2, 9, 2, COLORS.gold, 3);

        // Hands.
        ellipse(-13, -3, 3, 4, "#e9b68c");
        ellipse(13, -3, 3, 4, "#e9b68c");

        ctx.restore();

        if (nearestInteraction()?.data?.id === char.id) {
            drawInteractionMarker(x, y - 50);
        }
    }

    function drawPlayer() {
        const x = player.x * TILE;
        const y = player.y * TILE;

        const moving =
            state.keys.has("ArrowUp") ||
            state.keys.has("ArrowDown") ||
            state.keys.has("ArrowLeft") ||
            state.keys.has("ArrowRight") ||
            state.keys.has("w") ||
            state.keys.has("a") ||
            state.keys.has("s") ||
            state.keys.has("d");

        const bob = moving ? Math.sin(player.walkTime) * 2 : 0;

        ctx.save();
        ctx.translate(x, y + bob);

        ellipse(0, 11, 11, 4, COLORS.shadow);

        polygon([
            [-10, -4], [-8, -17], [8, -17],
            [11, 9], [-11, 9]
        ], "#3d6f91", "#214c6a");

        ellipse(0, -23, 9, 10, "#e9b68c", "#9a624e");

        // Hair.
        ellipse(0, -29, 9, 5, "#43232c");

        // Eyes.
        ellipse(-3, -23, 1.2, 1.4, "#2d1b25");
        ellipse(3, -23, 1.2, 1.4, "#2d1b25");

        // Sash.
        line(-7, -11, 7, 1, COLORS.gold, 3);

        ctx.restore();
    }

    /* ---------------- PARTICLES AND ANIMATION ---------------- */

    function createParticle() {
        return {
            x: Math.random() * W,
            y: H + Math.random() * 40,
            radius: 1 + Math.random() * 2.4,
            speed: 12 + Math.random() * 23,
            drift: (Math.random() - 0.5) * 14,
            alpha: 0.2 + Math.random() * 0.55
        };
    }

    for (let i = 0; i < 35; i++) {
        const p = createParticle();
        p.y = Math.random() * H;
        state.particles.push(p);
    }

    function updateParticles(dt) {
        for (const p of state.particles) {
            p.y -= p.speed * dt;
            p.x += p.drift * dt;

            if (p.y < -10) {
                Object.assign(p, createParticle());
            }

            if (p.x < -10) p.x = W + 10;
            if (p.x > W + 10) p.x = -10;
        }
    }

    function drawParticles() {
        for (const p of state.particles) {
            ctx.globalAlpha = p.alpha;
            ellipse(p.x, p.y, p.radius, p.radius, "#fff0b5");
        }

        ctx.globalAlpha = 1;
    }

    function drawDoorMarkers() {
        for (const door of roomDoors()) {
            const x = door.x * TILE + TILE / 2;
            const y = door.y * TILE + TILE / 2;

            // Small floor marker indicates a doorway.
            ellipse(x, y + 12, 17, 5, "#b47a3d");

            if (distance(player, door) < 1.8) {
                drawInteractionMarker(x, y - 30);
            }
        }
    }

    /* ---------------- RENDER LOOP ---------------- */

    function render() {
        ctx.clearRect(0, 0, W, H);

        drawRoomArchitecture();

        // Room-specific objects.
        for (const obj of activeObjects()) {
            drawObject(obj);
        }

        drawDoorMarkers();

        for (const char of activeCharacters()) {
            drawCharacter(char);
        }

        drawPlayer();
        drawParticles();

        // Room title.
        roundRect(18, 18, 245, 35, 8, "#351b32d9", COLORS.gold);
        text(ROOM_NAMES[state.room], 140, 36, 15, COLORS.cream);

        // Interaction prompt.
        const target = nearestInteraction();

        if (target && !state.dialogOpen &&
            !state.cinematicOpen && !state.levelOpen) {
            roundRect(285, 480, 390, 39, 9, "#351b32eF", COLORS.gold);

            const label = target.type === "door"
                ? "E — Enter " + target.data.label
                : "E — Interact: " + target.data.name;

            text(label, 480, 500, 14, COLORS.cream);
        }
    }

    function updateCamera(dt) {
        // The current room fits the screen. Camera interpolation is retained
        // as a reusable foundation for future scrolling levels.
        const targetX = 0;
        const targetY = 0;
        const smoothing = 1 - Math.exp(-5 * dt);

        state.camera.x += (targetX - state.camera.x) * smoothing;
        state.camera.y += (targetY - state.camera.y) * smoothing;
    }

    function getMovement() {
        let dx = 0;
        let dy = 0;

        if (state.keys.has("ArrowLeft") || state.keys.has("a")) dx--;
        if (state.keys.has("ArrowRight") || state.keys.has("d")) dx++;
        if (state.keys.has("ArrowUp") || state.keys.has("w")) dy--;
        if (state.keys.has("ArrowDown") || state.keys.has("s")) dy++;

        return { dx, dy };
    }

    function frame(timestamp) {
        if (!state.running) return;

        const dt = state.lastTime
            ? Math.min((timestamp - state.lastTime) / 1000, 0.05)
            : 0;

        state.lastTime = timestamp;
        state.elapsed += dt;

        if (state.toastTimer > 0) {
            state.toastTimer -= dt;

            if (state.toastTimer <= 0) {
                $("toast").classList.remove("visible");
            }
        }

        updateParticles(dt);
        updateCamera(dt);

        if (!state.dialogOpen && !state.cinematicOpen && !state.levelOpen) {
            const { dx, dy } = getMovement();
            movePlayer(dx, dy, dt);
        }

        render();
        updateHUD();

        requestAnimationFrame(frame);
    }

    /* ---------------- KEYBOARD INPUT ---------------- */

    function isTextInput(target) {
        return target instanceof HTMLInputElement ||
            target instanceof HTMLTextAreaElement ||
            target.isContentEditable;
    }

    window.addEventListener("keydown", event => {
        if (isTextInput(event.target)) return;

        const key = event.key.toLowerCase();

        if ([
            "ArrowUp", "ArrowDown", "ArrowLeft", "ArrowRight",
            " ", "Enter"
        ].includes(event.key)) {
            event.preventDefault();
        }

        if (key === "m") {
            $("audioButton").click();
            return;
        }

        if (key === "escape") {
            if (state.dialogOpen) closeDialog();
            return;
        }

        if (key === " " || key === "enter") {
            if (event.repeat) return;

            if (state.cinematicOpen) {
                nextCinematicScene();
            } else if (state.dialogOpen) {
                closeDialog();
            } else if (key === "enter") {
                safeInteract();
            }

            return;
        }

        if (["arrowup", "arrowdown", "arrowleft", "arrowright",
             "w", "a", "s", "d"].includes(key)) {
            state.keys.add(
                key.startsWith("arrow") ? event.key : key
            );
        }

        if (key === "e" && !event.repeat) {
            safeInteract();
        }
    });

    window.addEventListener("keyup", event => {
        const key = event.key.toLowerCase();

        state.keys.delete(event.key);
        state.keys.delete(key);
    });

    window.addEventListener("blur", () => {
        state.keys.clear();
    });

    /* ---------------- TOUCH INPUT ---------------- */

    const directionKeys = {
        up: "ArrowUp",
        down: "ArrowDown",
        left: "ArrowLeft",
        right: "ArrowRight"
    };

    document.querySelectorAll("[data-move]").forEach(button => {
        const direction = button.dataset.move;
        const key = directionKeys[direction];

        button.addEventListener("pointerdown", event => {
            event.preventDefault();
            button.setPointerCapture?.(event.pointerId);
            state.keys.add(key);
        });

        const release = event => {
            event.preventDefault();
            state.keys.delete(key);
        };

        button.addEventListener("pointerup", release);
        button.addEventListener("pointercancel", release);
        button.addEventListener("lostpointercapture", () => {
            state.keys.delete(key);
        });
    });

    $("interactButton").addEventListener("click", safeInteract);

    $("spaceButton").addEventListener("click", () => {
        if (state.cinematicOpen) {
            nextCinematicScene();
        } else if (state.dialogOpen) {
            closeDialog();
        } else {
            safeInteract();
        }
    });

    /* ---------------- RESTART ---------------- */

    function restartGame() {
        state.room = "exterior";
        state.discoveries.clear();
        state.visitedRooms = new Set(["exterior"]);

        state.cinematicTimer = 0;
        state.cinematicIndex = 0;
        state.cinematicStarted = false;
        state.cinematicFinished = false;
        state.cinematicOpen = false;
        state.dialogOpen = false;
        state.levelOpen = false;
        state.levelUnlocked = false;

        state.keys.clear();

        player.x = 3;
        player.y = 15;
        player.facing = "right";
        player.walkTime = 0;

        $("dialogOverlay").classList.remove("visible");
        $("cinematicOverlay").classList.remove("visible");
        $("levelOverlay").classList.remove("visible");

        updateHUD();
        canvas.focus();
        showToast("Welcome to Ayodhya!");
    }

    /* ---------------- STARTUP ---------------- */

    function runSelfChecks() {
        const checks = [
            ["Canvas dimensions", canvas.width === 960 && canvas.height === 540],
            ["32 x 18 grid", COLS === 32 && ROWS === 18],
            ["Tile size", TILE === 30],
            ["Five rooms", ROOM_ORDER.length === 5],
            ["Room names", ROOM_ORDER.every(key => Boolean(ROOM_NAMES[key]))],
            ["Royal cradle exists", objects.some(o => o.id === "royal_cradle")],
            ["Four cinematic scenes", cinematicScenes.length === 4],
            ["Level unlock state", typeof state.levelUnlocked === "boolean"]
        ];

        const failures = checks.filter(check => !check[1]);

        if (failures.length) {
            console.error("Game self-check failures:", failures);
        } else {
            console.info(
                "Game startup self-checks passed:",
                checks.length,
                "checks."
            );
        }
    }

    updateAudioButton();
    updateHUD();
    runSelfChecks();

    requestAnimationFrame(frame);

})();
</script>
</body>
</html>
```

## 3\. Important correction before testing

The game above contains the complete structure, but a reliable prototype also needs careful testing of the exploration flow. In particular, the royal cradle interaction must consistently launch the cinematic after the cradle's description has been discovered.

To make that behavior deterministic, **replace the existing****`interact()`****function and the****`interactWithCradle()`****/****`safeInteract()`****functions with the single implementation below**. This avoids overlapping interaction logic and makes the cradle trigger explicit.

```
function safeInteract() {
    if (state.dialogOpen) {
        closeDialog();
        return;
    }

    if (state.cinematicOpen) {
        nextCinematicScene();
        return;
    }

    if (state.levelOpen) return;

    initAudio();

    const target = nearestInteraction();

    if (!target) {
        showToast("Explore nearby objects, characters, and doors.");
        return;
    }

    if (target.type === "door") {
        transitionRoom(target.data);
        return;
    }

    if (target.type === "character") {
        const char = target.data;

        if (char.id === "dasharatha") {
            state.discoveries.add("dasharatha_met");
        }

        if (char.id === "kaushalya") {
            state.discoveries.add("kaushalya_met");
        }

        openDialog(char.title, char.text);
        updateHUD();
        return;
    }

    if (target.type === "object") {
        const obj = target.data;

        // On the second interaction, the discovered cradle starts the cinematic.
        if (obj.id === "royal_cradle" &&
            state.discoveries.has("royal_cradle") &&
            !state.cinematicFinished) {
            startCinematic();
            return;
        }

        if (!state.discoveries.has(obj.id)) {
            state.discoveries.add(obj.id);
            playBell();
        }

        openDialog(obj.title, obj.text);

        if (obj.id === "royal_cradle") {
            $("dialogHint").textContent =
                "Close this message and interact with the cradle again to begin the celebration.";
        }

        updateHUD();
    }
}
```

After replacing the functions, you can leave the rest of the HTML file unchanged. The second interaction with the discovered cradle will start the cinematic.

## 4\. How the game systems work

| System | Implementation |
| --- | --- |
| Rendering | HTML5 Canvas with JavaScript vector shapes |
| Grid | 32 columns × 18 rows |
| World units | 1 tile = 30 pixels in the rendered scene |
| Movement | Keyboard and pointer-based touch controls |
| Collision | Axis-separated movement checks against boundaries and furniture |
| Interactions | Proximity checks against characters, objects, and doors |
| Room transitions | Door-linked room definitions |
| Animation | Time-based sine functions, moving particles, and animated flags |
| Cinematic | Four story scenes with manual advancement |
| Audio | Optional Web Audio API oscillators |
| Progress | A set of discovered objects and a Level 2 unlock flag |
| Camera | Interpolation foundation for future scrolling levels |

### Story progression

1. **Palace Exterior:** Discover the royal banner.
2. **Royal Courtyard:** Inspect the lotus fountain and meet an attendant.
3. **Main Throne Hall:** Discover the throne and meet King Dasharatha.
4. **Queen's Chamber:** Meet Queen Kaushalya and discover the royal cradle.
5. **Birth Celebration:** Interact with the discovered cradle again to launch the cinematic.
6. **Success:** Complete the four cinematic scenes to unlock Level 2.

The five required rooms are connected by doors, and the player can return to previous rooms.

## 5\. Verification checklist

I have included startup self-checks in the JavaScript, but those checks are not a substitute for browser testing. Use the following checklist to validate the prototype:

- [ ]The page loads without a JavaScript syntax error.
- [ ]The console reports eight successful startup checks.
- [ ]The player moves with WASD and the arrow keys.
- [ ]The player cannot leave the room boundaries or walk through the throne and cradle.
- [ ]Pressing `E` near an object opens its story dialogue.
- [ ]Door interactions correctly transition between the five rooms.
- [ ]Discovering the royal cradle and interacting with it again starts the cinematic.
- [ ]Advancing through all four scenes displays the Level 2 unlock screen.
- [ ]The restart button resets the game to the Palace Exterior.
- [ ]Audio can be enabled and disabled without interrupting gameplay.
- [ ]Touch controls work on a mobile browser.

**One limitation to keep in mind:** This is an introductory playable prototype, not a finished commercial game. Level 2 is only marked as unlocked; its gameplay has not been implemented. The flute-like audio is synthesized rather than a recording of a real flute, and the four princes are introduced through the cinematic text rather than a fully animated group of four infant characters.

**Next step:** I can help you add a fully illustrated, animated cinematic featuring all four infant princes, or expand the prototype into a larger palace adventure with scrolling levels and a more advanced camera system.
