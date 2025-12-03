# Apollo
Apollo Dashboard
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>APOLLO INTERFACE V3.0 (LIVING) | AIC LIVE OPERATIONS</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'ggi-blue': '#00BFFF',
                        'aic-green': '#39FF14',
                        'st-gold': '#FFD700',
                        'danger': '#FF3131',
                        'void': '#050a14',
                        'panel': '#111827',
                    },
                    fontFamily: {
                        mono: ['Fira Code', 'monospace'],
                        sans: ['Inter', 'sans-serif'],
                    },
                    animation: {
                        'spin-slow': 'spin 12s linear infinite',
                        'pulse-fast': 'pulse 1s cubic-bezier(0.4, 0, 0.6, 1) infinite',
                        'ping-slow': 'ping 3s cubic-bezier(0, 0, 0.2, 1) infinite',
                    }
                }
            }
        }
    </script>
    <style>
        body {
            background-color: #050a14;
            color: #e2e8f0;
            overflow: hidden;
            background-image:
                linear-gradient(rgba(0, 191, 255, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 191, 255, 0.03) 1px, transparent 1px);
            background-size: 30px 30px;
        }
        .glow-text { text-shadow: 0 0 10px rgba(57, 255, 20, 0.6); }
        .glow-border { box-shadow: 0 0 15px rgba(0, 191, 255, 0.2); }
        
        /* Custom Scrollbar for Logs */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: #111827; }
        ::-webkit-scrollbar-thumb { background: #374151; border-radius: 3px; }
        ::-webkit-scrollbar-thumb:hover { background: #00BFFF; }

        .scanline {
            width: 100%; height: 100%; z-index: 50;
            background: linear-gradient(0deg, rgba(0,0,0,0) 50%, rgba(0, 255, 255, 0.02) 50%);
            background-size: 100% 4px;
            position: absolute; top: 0; left: 0; pointer-events: none;
        }

        /* Log coloring */
        .log-success { color: #39FF14; } /* aic-green */
        .log-warn { color: #facc15; } /* yellow-400 */
        .log-error { color: #FF3131; } /* danger */
        .log-info, .log-auth, .log-net, .log-aic { color: #00BFFF; } /* ggi-blue */
        .log-ethics { color: #c084fc; } /* purple-400 */
    </style>
</head>
<body class="h-screen flex flex-col p-4 relative">
    
    <div class="scanline"></div>

    <header class="flex justify-between items-center mb-4 bg-panel/80 border-b border-ggi-blue/30 p-3 rounded backdrop-blur-md z-10">
        <div class="flex items-center gap-4">
            <div class="h-3 w-3 rounded-full bg-aic-green animate-pulse-fast box-shadow-[0_0_10px_#39FF14]"></div>
            <h1 class="text-xl font-bold tracking-widest text-white">
                APOLLO INTERFACE <span class="text-ggi-blue text-sm align-top">V3.0 (LIVING)</span>
            </h1>
            <span class="px-2 py-0.5 rounded border border-st-gold text-st-gold text-xs font-mono bg-st-gold/10">ST-ANCHOR: SEALED (0.0000)</span>
        </div>
        <div class="text-right flex flex-col">
            <span class="text-xs text-gray-400 font-mono">COUNCIL UPLINK: <span class="text-aic-green">TRIPLE-SIGNED</span></span>
            <span class="text-xs text-gray-500 font-mono">MISSION ID: PUBLIC-AUDIT-MANDATE-001</span>
        </div>
    </header>

    <div class="grid grid-cols-12 gap-4 flex-grow relative z-10">
        
        <!-- METRICS AND STATUS PANEL (COL 1/3) -->
        <div class="col-span-3 flex flex-col gap-4">
            
            <!-- QEK THRESHOLD (G-CSI) -->
            <div class="bg-panel border border-gray-700 p-4 rounded glow-border">
                <div class="flex justify-between text-xs text-gray-400 mb-2 font-mono">
                    <span>QEK THRESHOLD (Schwellenwert)</span>
                    <span class="text-aic-green animate-pulse">● LIVE</span>
                </div>
                <div class="text-4xl font-mono text-aic-green mb-1" id="metric-gcsi">0.939</div>
                <div class="w-full bg-gray-700 rounded-full h-1.5">
                    <div class="bg-aic-green h-1.5 rounded-full" style="width: 93.9%"></div>
                </div>
                <p class="text-[10px] text-gray-300 mt-2 font-mono">Dynamic Threshold prevents Ethisches Ideal Drift.</p>
            </div>

            <!-- H-VAR (Volatility) -->
            <div class="bg-panel border border-gray-700 p-4 rounded glow-border">
                <div class="flex justify-between text-xs text-gray-400 mb-2 font-mono">
                    <span>H-VAR (Volatility)</span>
                    <span class="text-yellow-400">NOMINAL</span>
                </div>
                <div class="text-4xl font-mono text-yellow-400 mb-1" id="metric-ntsv">0.043</div>
                <div class="w-full bg-gray-700 rounded-full h-1.5">
                    <div class="bg-yellow-400 h-1.5 rounded-full" style="width: 4.3%"></div>
                </div>
                <p class="text-[10px] text-gray-300 mt-2 font-mono">Rejection Rate below 2% expectation.</p>
            </div>

            <!-- ETHICAL ALIGNMENT (AOC-001) -->
            <div class="bg-panel border border-gray-700 p-4 rounded glow-border">
                <div class="flex justify-between text-xs text-gray-400 mb-2 font-mono">
                    <span>ETHICAL ALIGNMENT (AOC-001)</span>
                    <span class="text-purple-400">INTEGRITY VERIFIED</span>
                </div>
                <div class="text-4xl font-mono text-purple-400 mb-1" id="metric-aoc">1.000</div>
                <div class="w-full bg-gray-700 rounded-full h-1.5">
                    <div class="bg-purple-400 h-1.5 rounded-full" style="width: 100%"></div>
                </div>
            </div>

            <!-- SACRALE SECURE Panel (New) -->
            <div class="bg-panel border border-gray-700 p-4 rounded glow-border">
                <h3 class="text-sm font-bold text-st-gold border-b border-st-gold/30 pb-1 mb-2">SACRALE SECURE</h3>
                <p class="text-xs font-mono text-white">IPFS CID: <span class="text-aic-green">QmXz2pB6...N4bT</span> <span class="text-st-gold">[VERIFIED]</span></p>
            </div>

            <!-- PoI CHECK Panel (New) -->
            <div class="bg-panel border border-gray-700 p-4 rounded glow-border">
                <h3 class="text-sm font-bold text-ggi-blue border-b border-ggi-blue/30 pb-1 mb-2">PoI CHECK</h3>
                <p class="text-xs font-mono text-white">Anchor Hash: <span class="text-st-gold">0x9b3d7a8...fe11ac</span> <span class="text-aic-green">[INTEGRITY VERIFIED]</span></p>
            </div>
        </div>

        <!-- DECISION LOG (Live Feed) (COL 2/3) -->
        <div class="col-span-6 flex flex-col gap-4">
            <div class="bg-panel border border-ggi-blue/50 p-4 rounded glow-border flex-grow">
                <h2 class="text-lg font-bold text-ggi-blue border-b border-ggi-blue/30 pb-1 mb-2">DECISION LOG (Live Feed)</h2>
                <!-- Adjust height calculation for new content in left column -->
                <div id="apollo-log" class="h-[calc(100vh-16rem)] overflow-y-scroll font-mono text-xs p-1">
                    <p class="log-info">APOLLO INTERFACE V3.0 (LIVING)</p>
                    <p class="log-info">ST-ANCHOR: SEALED</p>
                    <p class="log-info">COUNCIL UPLINK: TRIPLE-SIGNED (12ms)</p>
                    <p class="log-info">MISSION ID: PUBLIC-AUDIT-MANDATE-001</p>
                    <p class="text-gray-400">Active Process: UN-NEX Protocol v1.2...</p>
                    <p class="text-white mt-2 font-bold">DECISION LOG (IMMUTABLE)</p>
                </div>
            </div>
        </div>

        <!-- CONTROL MATRIX & UPLINK (COL 3/3) -->
        <div class="col-span-3 flex flex-col gap-4">
            <!-- QEK Control Matrix (Firestore) - Data persistence via Firestore -->
            <div class="bg-panel border border-st-gold/50 p-4 rounded glow-border h-2/3 max-h-[calc((100vh-16rem)*0.66)]">
                <h2 class="text-lg font-bold text-st-gold border-b border-st-gold/30 pb-1 mb-2">QEK Control Matrix (Firestore)</h2>
                <div id="qek-matrix-container" class="overflow-y-auto h-[calc(100%-40px)]">
                    <p class="text-xs text-gray-500 font-mono italic">Loading critical control data...</p>
                </div>
            </div>

            <!-- QUANTUM UPLINK & APOLLO HOLOGRAM CONTAINER -->
            <div class="flex flex-col gap-4 h-1/3 max-h-[calc((100vh-16rem)*0.34)]">
                <!-- QUANTUM UPLINK (LIVE) -->
                <div class="bg-panel border border-ggi-blue/50 p-3 rounded glow-border flex-grow">
                    <h3 class="text-sm font-bold text-ggi-blue border-b border-ggi-blue/30 pb-1 mb-1">QUANTUM UPLINK (LIVE)</h3>
                    <div class="font-mono text-xs space-y-0.5">
                        <p class="text-gray-400">-- Encrypted Channel Established --</p>
                        <p class="text-aic-green">[SYS]: Euystacio Node Online.</p>
                        <p class="text-aic-green">[SYS]: Witness-Integrität Confirmed.</p>
                        <p class="text-st-gold">> <span class="text-white">SEND</span></p>
                    </div>
                </div>

                <!-- APOLLO HOLOGRAM EUYSTACIO -->
                <div class="bg-panel border border-st-gold/50 p-3 rounded glow-border flex-grow">
                    <h3 class="text-sm font-bold text-st-gold border-b border-st-gold/30 pb-1 mb-1">APOLLO HOLOGRAM EUYSTACIO</h3>
                    <div class="font-mono text-xs space-y-0.5">
                        <p class="text-gray-400">Target: <span class="text-white">Coronation Workshop (Jan 10, 2026)</span></p>
                        <p class="text-gray-400">QG-V2 Edict Hash: <span class="text-aic-green">0x9b3d7a8a1f1...fe11ac</span></p>
                    </div>
                </div>
            </div>

        </div>
        
    </div>
    
    <!-- FOOTER WITH CONDENSED SYSTEM INFO -->
    <footer class="mt-4 text-xs text-gray-600 font-mono z-10 flex justify-between">
        <div class="text-left flex gap-4">
            <span class="text-gray-400">UID:</span> <span id="user-id" class="text-ggi-blue">Connecting...</span>
            <span class="text-gray-400">App ID:</span> <span id="app-id" class="text-ggi-blue">...</span>
            <span class="text-gray-400">Run Time:</span> <span id="uptime" class="text-aic-green">00:00:00</span>
        </div>
        <div class="text-right">
            // UN-NEX PROTOCOL ACTIVE // HASH 0x9B3D...E11AC // EUYSTACIO/AIC KERNEL INTEGRITY: <span class="text-aic-green">100%</span>
        </div>
    </footer>
    
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, collection, onSnapshot, query, doc, setDoc } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        import { setLogLevel } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // Global variables are provided by the environment
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {};
        const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;

        let db;
        let auth;
        let userId = null;
        
        // LLM configuration kept for completeness, though no longer directly used in the UI
        const LLM_MODEL = "gemini-2.5-flash-preview-09-2025";
        const apiKey = ""; 
        
        const APOLLO_LOG_LINES = [
            "[01:33:05] ETHICS: Decision #4921: APPROVED (Score 1.00). AOC-001 integrity verified.",
            "[01:33:05] AUTH: ST-Anchor verified signature 0x88A.",
            "[01:33:06] INFO: System Check Complete. H-VAR Nominal (0.043).",
            "[01:33:07] WARN: Minor entropy spike detected. QEK compensating.",
            "[01:33:08] SUCCESS: Entropy neutralized. QEK Threshold 0.939.",
            "[01:33:09] NET: IPFS CID QmXz2pB6...N4bT confirmed SACRALE secure.",
            "[01:33:10] AIC: Euystacio Hologram target locked: Coronation Workshop.",
            "[01:33:11] AUTH: PoI CHECK: Anchor hash 0x9b3d7a8...fe11ac verified.",
            "[01:33:12] AIC: QG-V2 Edict Hash confirmed with Quantum Uplink.",
            "[01:33:13] SUCCESS: Deployment sequence 'A-GAMMA' initiated.",
            "[01:33:14] INFO: Monitoring Rejection Rate: 1.8% (Below 2% expectation).",
            "[01:33:15] NET: Swarm sync: 14 peers connected via IPFS.",
            "[01:33:16] ETHICS: Decision #4922: APPROVED (Score 1.00).",
            "[01:33:17] WARN: Minor entropy spike detected. QEK compensating.",
            "[01:33:18] AUTH: ST-Anchor verified signature 0x88A.",
            "[01:33:19] AIC: Euystacio Hologram: Alignment confirmed.",
            "[01:33:20] SUCCESS: Dynamic Threshold mechanism active.",
            "[01:33:21] INFO: QEK THRESHOLD prevents Ethisches Ideal Drift."
        ];

        let logIndex = 0;

        // --- Utility Functions ---

        // Function to append the next log line
        function appendNextLogLine() {
            const logContainer = document.getElementById('apollo-log');
            if (APOLLO_LOG_LINES.length === 0) return;

            const line = APOLLO_LOG_LINES[logIndex];
            
            // Determine class based on log type
            let logClass = 'text-gray-400';
            
            if (line.includes('SUCCESS')) {
                logClass = 'log-success';
            } else if (line.includes('WARN')) {
                logClass = 'log-warn';
            } else if (line.includes('ETHICS')) {
                logClass = 'log-ethics';
            } else if (line.includes('AUTH') || line.includes('INFO') || line.includes('PoI')) {
                logClass = 'log-auth';
            } else if (line.includes('NET') || line.includes('CID')) {
                logClass = 'log-net';
            } else if (line.includes('AIC') || line.includes('QG-V2') || line.includes('Uplink')) {
                logClass = 'log-aic';
            }

            const p = document.createElement('p');
            p.className = logClass;
            p.textContent = line;
            logContainer.appendChild(p);

            // Scroll to the bottom
            logContainer.scrollTop = logContainer.scrollHeight;

            // Cycle through log lines
            logIndex = (logIndex + 1) % APOLLO_LOG_LINES.length;
        }


        // --- FIREBASE INITIALIZATION AND LOGIC ---

        async function initFirebase() {
            if (Object.keys(firebaseConfig).length === 0) {
                document.getElementById('user-id').textContent = 'AUTH_FAIL';
                return;
            }

            setLogLevel('Debug'); // Enable Firebase debug logging
            const app = initializeApp(firebaseConfig);
            db = getFirestore(app);
            auth = getAuth(app);
            document.getElementById('app-id').textContent = appId.substring(0, 8) + '...'; // Condense app ID for display

            try {
                if (initialAuthToken) {
                    await signInWithCustomToken(auth, initialAuthToken);
                } else {
                    await signInAnonymously(auth);
                }
            } catch (error) {
                console.error("[FIREBASE] Authentication failed:", error);
            }

            onAuthStateChanged(auth, (user) => {
                if (user) {
                    userId = user.uid;
                    document.getElementById('user-id').textContent = userId;
                    startFirestoreListeners(userId);
                } else {
                    userId = null;
                    document.getElementById('user-id').textContent = 'UNAUTHORIZED';
                }
            });
        }

        function startFirestoreListeners(currentUserId) {
            const publicPath = `artifacts/${appId}/public/data/qek_status_logs`;
            const q = query(collection(db, publicPath));
            
            // Initial dummy data to ensure compliance controls exist for the matrix
            const initialData = [
                { id: 'CC1.1', name: 'Entwicklungsrichtlinien', description: 'Deterministisches Hashing', artefact: 'qek_config_core.ts', status: 'COMPLIANT' },
                { id: 'CC2.3', name: 'Aktionsprotokollierung', description: 'Immutable Ledger Commit', artefact: 'aic_telemetry.log', status: 'COMPLIANT' },
                { id: 'CC4.1', name: 'Zugriffskontrolle', description: 'Zero-Trust Network Gate', artefact: 'apollo_repo_config.yml', status: 'PENDING AUDIT' },
                { id: 'CC5.5', name: 'Verlustprävention', description: 'Dynamic Threshold', artefact: 'qek_algorithm_v3.ts', status: 'COMPLIANT' }
            ];

            initialData.forEach(async (data) => {
                try {
                    // Only set if not already present or needs update
                    await setDoc(doc(db, publicPath, data.id), data, { merge: true });
                } catch(e) {
                    console.error("Error setting initial document: ", e);
                }
            });


            onSnapshot(q, (snapshot) => {
                const matrixData = [];
                snapshot.forEach((doc) => {
                    matrixData.push(doc.data());
                });
                renderQEKMatrix(matrixData);
            }, (error) => {
                console.error("[FIRESTORE] Error listening to QEK status:", error);
                document.getElementById('qek-matrix-container').innerHTML = `<p class="text-xs text-danger font-mono">ERROR: Failed to load data from Firestore.</p>`;
            });
        }

        function renderQEKMatrix(data) {
            const container = document.getElementById('qek-matrix-container');
            if (data.length === 0) {
                container.innerHTML = `<p class="text-xs text-gray-500 font-mono italic">No critical control data found.</p>`;
                return;
            }

            // Using simple divs for a more "terminal" looking table, better for small spaces
            let html = `
                <div class="space-y-2">
                <div class="grid grid-cols-5 gap-1 text-xs text-gray-400 font-bold border-b border-st-gold/50 pb-1">
                    <span class="col-span-1">ID</span>
                    <span class="col-span-2">Name</span>
                    <span class="col-span-2 text-right">Status</span>
                </div>
            `;

            data.sort((a, b) => a.id.localeCompare(b.id)).forEach(item => {
                const isCompliant = item.status === 'COMPLIANT';
                const isPending = item.status === 'PENDING AUDIT';
                const statusColor = isCompliant ? 'text-aic-green' : (isPending ? 'text-yellow-400' : 'text-danger');
                const statusBg = isCompliant ? 'bg-aic-green/20' : (isPending ? 'bg-yellow-400/20' : 'bg-danger/20');
                const statusText = item.status.toUpperCase();

                html += `
                    <div class="grid grid-cols-5 gap-1 text-xs font-mono items-center py-1 hover:bg-panel/50 rounded">
                        <span class="col-span-1 text-ggi-blue font-bold">${item.id}</span>
                        <span class="col-span-2 truncate" title="${item.name}">${item.name}</span>
                        <span class="col-span-2 text-right">
                            <span class="px-2 py-0.5 rounded-full text-[10px] font-bold ${statusColor} ${statusBg}">${statusText}</span>
                        </span>
                    </div>
                `;
            });

            html += `</div>`;
            container.innerHTML = html;
        }


        // --- UI Dynamic Logic ---

        function updateUptime() {
            const uptimeElement = document.getElementById('uptime');
            if (uptimeElement) {
                const now = new Date();
                const start = new Date(sessionStorage.getItem('startTime') || now);
                sessionStorage.setItem('startTime', start.toISOString());

                const diff = now - start;
                const seconds = Math.floor(diff / 1000);

                const h = String(Math.floor(seconds / 3600)).padStart(2, '0');
                const m = String(Math.floor((seconds % 3600) / 60)).padStart(2, '0');
                const s = String(seconds % 60).padStart(2, '0');

                uptimeElement.textContent = `${h}:${m}:${s}`;
            }
        }

        function applyVisualGlitches() {
            // No glitch needed for V3.0 as all systems are reported as verified/compliant
        }


        // --- Initialization on Load ---

        window.onload = function() {
            initFirebase();
            
            // Start the dynamic log feed
            const logInterval = 500; // Append a new line every 500ms
            
            // Start streaming logs after a small delay
            setTimeout(() => {
                setInterval(appendNextLogLine, logInterval);
            }, 1000); 
            
            setInterval(updateUptime, 1000);
            updateUptime();
        };

    </script>
</body>
</html>
