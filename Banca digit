<!DOCTYPE html>
<html lang="ro" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Volt Bank - Fintech Experience</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Chart.js for Analytics -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- Tailwind Config for Custom Theme -->
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        brand: {
                            50: '#eef2ff',
                            100: '#e0e7ff',
                            500: '#6366f1',
                            600: '#4f46e5',
                            700: '#4338ca',
                            accent: '#00d2ff'
                        },
                        darkbg: '#0f172a',
                        darkcard: '#1e293b',
                        darkborder: '#334155'
                    }
                }
            }
        }
    </script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap');
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
        }
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: rgba(15, 23, 42, 0.6);
        }
        ::-webkit-scrollbar-thumb {
            background: #334155;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #475569;
        }
        /* Glassmorphism effects */
        .glass-card {
            background: rgba(30, 41, 59, 0.7);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.08);
        }
        .light .glass-card {
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(0, 0, 0, 0.08);
        }
        /* Card Flip Effect */
        .perspective-1000 {
            perspective: 1000px;
        }
        .card-inner {
            transition: transform 0.6s;
            transform-style: preserve-3d;
        }
        .card-flipped {
            transform: rotateY(180deg);
        }
        .card-front, .card-back {
            backface-visibility: hidden;
        }
        .card-back {
            transform: rotateY(180deg);
        }
    </style>
</head>
<body class="bg-slate-950 text-slate-100 min-h-screen flex flex-col md:flex-row antialiased selection:bg-brand-500 selection:text-white transition-colors duration-300 light:bg-slate-50 light:text-slate-800">

    <!-- Toast Notification Container -->
    <div id="toast-container" class="fixed top-5 right-5 z-50 flex flex-col gap-3 pointer-events-none max-w-sm w-full px-4"></div>

    <!-- Sidebar Navigation for Desktop -->
    <aside class="hidden md:flex flex-col w-64 bg-slate-900/80 border-r border-slate-800 p-5 space-y-8 sticky top-0 h-screen z-20 backdrop-blur-md">
        <!-- Logo -->
        <div class="flex items-center gap-3 px-2">
            <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-indigo-600 via-brand-500 to-cyan-400 flex items-center justify-center text-white text-xl font-black shadow-lg shadow-indigo-500/30">
                V
            </div>
            <div>
                <span class="text-xl font-black tracking-wider bg-gradient-to-r from-white via-slate-200 to-slate-400 bg-clip-text text-transparent">VOLT</span>
                <span class="text-xs font-semibold px-2 py-0.5 rounded-full bg-indigo-500/20 text-indigo-400 border border-indigo-500/30 ml-1">PRO</span>
            </div>
        </div>

        <!-- User Profile Quick View -->
        <div class="flex items-center gap-3 p-3 rounded-2xl bg-slate-800/50 border border-slate-700/50">
            <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&q=80&w=200" alt="Avatar User" class="w-10 h-10 rounded-full object-cover ring-2 ring-indigo-500/50">
            <div class="overflow-hidden">
                <p class="text-sm font-semibold truncate">Alexandru Metin</p>
                <p class="text-xs text-slate-400 truncate">@alexandru.volt</p>
            </div>
        </div>

        <!-- Navigation Links -->
        <nav class="flex-1 space-y-1">
            <button onclick="switchTab('dashboard')" id="nav-dashboard" class="nav-btn w-full flex items-center gap-3 px-4 py-3 rounded-xl font-medium transition-all text-brand-500 bg-indigo-500/10 border border-indigo-500/20">
                <i class="fa-solid fa-chart-pie text-lg"></i>
                <span>Panou Principal</span>
            </button>
            <button onclick="switchTab('cards')" id="nav-cards" class="nav-btn w-full flex items-center gap-3 px-4 py-3 rounded-xl font-medium text-slate-400 hover:text-slate-200 hover:bg-slate-800/50 transition-all">
                <i class="fa-solid fa-credit-card text-lg"></i>
                <span>Carduri Virtuale</span>
            </button>
            <button onclick="switchTab('analytics')" id="nav-analytics" class="nav-btn w-full flex items-center gap-3 px-4 py-3 rounded-xl font-medium text-slate-400 hover:text-slate-200 hover:bg-slate-800/50 transition-all">
                <i class="fa-solid fa-chart-line text-lg"></i>
                <span>Analiză Spends</span>
            </button>
            <button onclick="switchTab('exchange')" id="nav-exchange" class="nav-btn w-full flex items-center gap-3 px-4 py-3 rounded-xl font-medium text-slate-400 hover:text-slate-200 hover:bg-slate-800/50 transition-all">
                <i class="fa-solid fa-right-left text-lg"></i>
                <span>Schimb Valutar</span>
            </button>
        </nav>

        <!-- Theme Toggle & Support -->
        <div class="pt-4 border-t border-slate-800 space-y-2">
            <button onclick="toggleTheme()" class="w-full flex items-center justify-between px-4 py-2.5 rounded-xl text-xs font-semibold bg-slate-800/40 hover:bg-slate-800 text-slate-300 border border-slate-700/50 transition-all">
                <span class="flex items-center gap-2"><i class="fa-solid fa-moon text-indigo-400"></i> Mod Întunecat</span>
                <span id="theme-status" class="text-[10px] bg-indigo-500/20 text-indigo-300 px-2 py-0.5 rounded-full">ACTIV</span>
            </button>
            <div class="p-3 rounded-xl bg-gradient-to-br from-indigo-900/30 to-purple-900/20 border border-indigo-500/20 text-xs">
                <p class="font-semibold text-indigo-300 mb-1"><i class="fa-solid fa-shield-halved mr-1"></i> Protecție FIDC</p>
                <p class="text-slate-400 text-[11px]">Fondurile tale sunt asigurate până la 100.000 EUR.</p>
            </div>
        </div>
    </aside>

    <!-- Mobile Header -->
    <header class="md:hidden flex items-center justify-between p-4 bg-slate-900/90 border-b border-slate-800 sticky top-0 z-30 backdrop-blur-md">
        <div class="flex items-center gap-3">
            <div class="w-8 h-8 rounded-lg bg-gradient-to-tr from-indigo-600 to-cyan-400 flex items-center justify-center text-white font-black text-sm">
                V
            </div>
            <span class="font-bold text-lg tracking-wide">VOLT</span>
        </div>
        <div class="flex items-center gap-2">
            <button onclick="toggleTheme()" class="p-2 rounded-lg bg-slate-800 text-slate-300 text-sm">
                <i class="fa-solid fa-circle-half-stroke"></i>
            </button>
            <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&q=80&w=200" alt="Avatar User" class="w-8 h-8 rounded-full ring-2 ring-indigo-500">
        </div>
    </header>

    <!-- Main Content Area -->
    <main class="flex-1 p-4 md:p-8 max-w-7xl mx-auto w-full pb-24 md:pb-8 overflow-y-auto">

        <!-- SECTION 1: DASHBOARD -->
        <div id="tab-dashboard" class="tab-content space-y-6">
            
            <!-- Greeting & Quick Stats -->
            <div class="flex flex-col md:flex-row md:items-center justify-between gap-4">
                <div>
                    <h1 class="text-2xl md:text-3xl font-extrabold tracking-tight">Salutare Alexandru Metin 👋</h1>
                    <p class="text-slate-400 text-sm mt-1">Iată o privire de ansamblu asupra finanțelor tale astăzi.</p>
                </div>
                <!-- Currency Switcher Pills -->

                    <p class="text-slate-400 text-sm mt-1">Iată o privire de ansamblu asupra finanțelor tale astăzi.</p>
                </div>
                <!-- Currency Switcher Pills -->
                <div class="flex items-center gap-2 bg-slate-900/80 p-1.5 rounded-2xl border border-slate-800 self-start md:self-auto">
                    <button onclick="changeCurrency('RON')" id="curr-btn-RON" class="curr-tab-btn px-4 py-2 rounded-xl text-xs font-bold transition-all bg-brand-500 text-white shadow-lg shadow-indigo-500/25">
                        🇷🇴 RON
                    </button>
                    <button onclick="changeCurrency('EUR')" id="curr-btn-EUR" class="curr-tab-btn px-4 py-2 rounded-xl text-xs font-bold transition-all text-slate-400 hover:text-white hover:bg-slate-800">
                        🇪🇺 EUR
                    </button>
                    <button onclick="changeCurrency('USD')" id="curr-btn-USD" class="curr-tab-btn px-4 py-2 rounded-xl text-xs font-bold transition-all text-slate-400 hover:text-white hover:bg-slate-800">
                        🇺🇸 USD
                    </button>
                </div>
            </div>

            <!-- Balance Card Showcase -->
            <div class="relative overflow-hidden rounded-3xl bg-gradient-to-br from-slate-900 via-indigo-950/60 to-slate-900 p-6 md:p-8 border border-indigo-500/20 shadow-2xl shadow-indigo-950/50">
                <!-- Decorative Glow Backgrounds -->
                <div class="absolute -right-16 -top-16 w-64 h-64 bg-indigo-500/10 rounded-full blur-3xl pointer-events-none"></div>
                <div class="absolute -left-16 -bottom-16 w-64 h-64 bg-cyan-500/10 rounded-full blur-3xl pointer-events-none"></div>

                <div class="relative z-10 flex flex-col md:flex-row justify-between items-start md:items-center gap-6">
                    <div>
                        <div class="flex items-center gap-2 text-slate-400 text-sm font-medium mb-1">
                            <span>Sold cont principal</span>
                            <span id="active-currency-label" class="px-2 py-0.5 rounded-full text-[10px] font-bold bg-indigo-500/20 text-indigo-300 border border-indigo-500/30">RON</span>
                        </div>
                        <div class="flex items-baseline gap-2">
                            <h2 id="main-balance-display" class="text-4xl md:text-5xl font-black tracking-tight text-white">
                                14.850,50
                            </h2>
                            <span id="main-currency-symbol" class="text-2xl font-bold text-indigo-400">RON</span>
                        </div>
                        <p class="text-xs text-emerald-400 font-medium mt-2 flex items-center gap-1">
                            <i class="fa-solid fa-arrow-trend-up"></i> +12.4% economii față de luna trecută
                        </p>
                    </div>

                    <!-- Action Buttons Bar -->
                    <div class="grid grid-cols-4 gap-3 w-full md:w-auto">
                        <button onclick="openModal('modal-send')" class="flex flex-col items-center justify-center p-3 rounded-2xl bg-indigo-600 hover:bg-indigo-500 text-white transition-all transform hover:-translate-y-1 shadow-lg shadow-indigo-600/30 group">
                            <div class="w-10 h-10 rounded-xl bg-white/10 flex items-center justify-center mb-1 group-hover:scale-110 transition-transform">
                                <i class="fa-solid fa-paper-plane text-sm"></i>
                            </div>
                            <span class="text-[11px] font-semibold">Trimite</span>
                        </button>

                        <button onclick="openModal('modal-topup')" class="flex flex-col items-center justify-center p-3 rounded-2xl bg-slate-800 hover:bg-slate-700 text-white border border-slate-700 transition-all transform hover:-translate-y-1 group">
                            <div class="w-10 h-10 rounded-xl bg-slate-700 flex items-center justify-center mb-1 group-hover:scale-110 transition-transform text-emerald-400">
                                <i class="fa-solid fa-plus text-sm"></i>
                            </div>
                            <span class="text-[11px] font-semibold">Alimentează</span>
                        </button>

                        <button onclick="switchTab('exchange')" class="flex flex-col items-center justify-center p-3 rounded-2xl bg-slate-800 hover:bg-slate-700 text-white border border-slate-700 transition-all transform hover:-translate-y-1 group">
                            <div class="w-10 h-10 rounded-xl bg-slate-700 flex items-center justify-center mb-1 group-hover:scale-110 transition-transform text-cyan-400">
                                <i class="fa-solid fa-arrows-rotate text-sm"></i>
                            </div>
                            <span class="text-[11px] font-semibold">Schimb</span>
                        </button>

                        <button onclick="switchTab('analytics')" class="flex flex-col items-center justify-center p-3 rounded-2xl bg-slate-800 hover:bg-slate-700 text-white border border-slate-700 transition-all transform hover:-translate-y-1 group">
                            <div class="w-10 h-10 rounded-xl bg-slate-700 flex items-center justify-center mb-1 group-hover:scale-110 transition-transform text-purple-400">
                                <i class="fa-solid fa-chart-simple text-sm"></i>
                            </div>
                            <span class="text-[11px] font-semibold">Rapoarte</span>
                        </button>
                    </div>
                </div>
            </div>

            <!-- Quick Multi-Currency Vault Overview -->
            <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                <div class="glass-card p-4 rounded-2xl flex items-center justify-between border border-slate-800">
                    <div class="flex items-center gap-3">
                        <div class="w-10 h-10 rounded-xl bg-blue-500/10 text-blue-400 flex items-center justify-center font-bold">🇷🇴</div>
                        <div>
                            <p class="text-xs text-slate-400 font-medium">Lei Românești</p>
                            <p id="vault-ron-val" class="text-base font-bold text-white">14.850,50 RON</p>
                        </div>
                    </div>
                    <span class="text-xs text-slate-500">Principal</span>
                </div>

                <div class="glass-card p-4 rounded-2xl flex items-center justify-between border border-slate-800">
                    <div class="flex items-center gap-3">
                        <div class="w-10 h-10 rounded-xl bg-emerald-500/10 text-emerald-400 flex items-center justify-center font-bold">🇪🇺</div>
                        <div>
                            <p class="text-xs text-slate-400 font-medium">Euro</p>
                            <p id="vault-eur-val" class="text-base font-bold text-white">1.240,00 EUR</p>
                        </div>
                    </div>
                    <button onclick="changeCurrency('EUR')" class="text-xs text-indigo-400 hover:underline">Vezi</button>
                </div>

                <div class="glass-card p-4 rounded-2xl flex items-center justify-between border border-slate-800">
                    <div class="flex items-center gap-3">
                        <div class="w-10 h-10 rounded-xl bg-amber-500/10 text-amber-400 flex items-center justify-center font-bold">🇺🇸</div>
                        <div>
                            <p class="text-xs text-slate-400 font-medium">Dolari SUA</p>
                            <p id="vault-usd-val" class="text-base font-bold text-white">850,00 USD</p>
                        </div>
                    </div>
                    <button onclick="changeCurrency('USD')" class="text-xs text-indigo-400 hover:underline">Vezi</button>
                </div>
            </div>

            <!-- Recent Transactions Section -->
            <div class="glass-card rounded-3xl p-6 border border-slate-800/80 space-y-4">
                <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3">
                    <div>
                        <h3 class="text-lg font-bold">Tranzacții Recente</h3>
                        <p class="text-xs text-slate-400">Istoricul activităților tale financiare</p>
                    </div>

                    <!-- Search & Category Filters -->
                    <div class="flex items-center gap-2 flex-wrap">
                        <div class="relative flex-1 sm:w-48">
                            <i class="fa-solid fa-magnifying-glass absolute left-3 top-1/2 -translate-y-1/2 text-slate-500 text-xs"></i>
                            <input type="text" id="tx-search" oninput="renderTransactions()" placeholder="Căutare..." class="w-full bg-slate-900/90 border border-slate-700/60 rounded-xl pl-8 pr-3 py-1.5 text-xs focus:outline-none focus:border-indigo-500 transition-all text-slate-200">
                        </div>
                        <select id="tx-category-filter" onchange="renderTransactions()" class="bg-slate-900/90 border border-slate-700/60 rounded-xl px-3 py-1.5 text-xs focus:outline-none focus:border-indigo-500 transition-all text-slate-200">
                            <option value="ALL">Toate Categoriile</option>
                            <option value="Shopping">Shopping</option>
                            <option value="Mâncare & Băuturi">Mâncare & Băuturi</option>
                            <option value="Transfer">Transferuri</option>
                            <option value="Abonamente">Abonamente</option>
                            <option value="Salariu">Salariu & Venituri</option>
                        </select>
                    </div>
                </div>

                <!-- Transactions List Container -->
                <div id="transactions-list" class="space-y-2 max-h-[420px] overflow-y-auto pr-1">
                    <!-- Dynamic Items render here -->
                </div>
            </div>
        </div>

        <!-- SECTION 2: VIRTUAL CARDS -->
        <div id="tab-cards" class="tab-content hidden space-y-6">
            <div>
                <h1 class="text-2xl md:text-3xl font-extrabold tracking-tight">Carduri Virtuale</h1>
                <p class="text-slate-400 text-sm mt-1">Gestionează cardurile tale securizate pentru plăți online rapide.</p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-start">
                
                <!-- Interactive 3D Card Display -->
                <div class="flex flex-col items-center">
                    <div class="perspective-1000 w-full max-w-sm h-56 cursor-pointer" onclick="flipCard()">
                        <div id="card-element" class="card-inner relative w-full h-full rounded-2xl shadow-2xl transition-transform duration-700">
                            
                            <!-- Front Side of Card -->
                            <div class="card-front absolute inset-0 rounded-2xl bg-gradient-to-tr from-slate-950 via-indigo-900 to-purple-800 p-6 flex flex-col justify-between border border-indigo-400/30 overflow-hidden shadow-2xl">
                                <div class="absolute -right-12 -top-12 w-40 h-40 bg-cyan-400/20 rounded-full blur-2xl"></div>
                                <div class="flex justify-between items-center z-10">
                                    <div class="flex items-center gap-2">
                                        <div class="w-8 h-8 rounded-lg bg-white/10 flex items-center justify-center font-black text-white text-xs">V</div>
                                        <span class="text-xs font-bold tracking-widest text-slate-200">VOLT ULTRA</span>
                                    </div>
                                    <i class="fa-solid fa-wifi text-slate-300 text-lg"></i>
                                </div>

                                <!-- Chip Icon -->
                                <div class="z-10 my-2">
                                    <div class="w-11 h-8 rounded-md bg-gradient-to-r from-amber-300 to-amber-500 opacity-90 border border-amber-200/50 flex items-center justify-center">
                                        <div class="w-full h-0.5 bg-amber-700/40"></div>
                                    </div>
                                </div>

                                <div class="z-10">
                                    <p id="card-number-display" class="font-mono text-lg tracking-widest text-white drop-shadow-md">
                                        •••• •••• •••• 8842
                                    </p>
                                    <div class="flex justify-between items-end mt-3">
                                        <div>
                                            <p class="text-[9px] uppercase tracking-wider text-slate-300">Titular Card</p>
                                            <p class="text-xs font-semibold text-white tracking-wide">ALEXANDRU METIN</p>
                                        </div>
                                        <div>
                                            <p class="text-[9px] uppercase tracking-wider text-slate-300">Expiră</p>
                                            <p class="text-xs font-semibold text-white">08/28</p>
                                        </div>
                                        <i class="fa-brands fa-cc-mastercard text-3xl text-white opacity-90"></i>
                                    </div>
                                </div>

                                        </div>
                                        <div>
                                            <p class="text-[9px] uppercase tracking-wider text-slate-300">Expiră</p>
                                            <p class="text-xs font-semibold text-white">08/28</p>
                                        </div>
                                        <i class="fa-brands fa-cc-mastercard text-3xl text-white opacity-90"></i>
                                    </div>
                                </div>
                            </div>

                            <!-- Back Side of Card -->
                            <div class="card-back absolute inset-0 rounded-2xl bg-slate-900 p-6 flex flex-col justify-between border border-slate-700 overflow-hidden">
                                <div class="w-full h-10 bg-slate-800 -mx-6 mt-2"></div>
                                <div class="space-y-2">
                                    <div class="bg-slate-200 text-slate-900 p-2 rounded text-right font-mono text-sm font-bold tracking-widest">
                                        CVV: <span id="card-cvv-display">•••</span>
                                    </div>
                                    <p class="text-[10px] text-slate-400">Card emis de Volt Bank SA sub licență internațională. A se folosi conform termenilor.</p>
                                </div>
                                <div class="text-right text-xs font-bold text-slate-500">VOLT DIGITAL</div>
                            </div>
                        </div>
                    </div>
                    <p class="text-xs text-slate-500 mt-3"><i class="fa-solid fa-rotate mr-1"></i> Apasă pe card pentru a-l roti</p>
                </div>

                <!-- Card Controls & Options -->
                <div class="glass-card rounded-3xl p-6 border border-slate-800 space-y-6">
                    <h3 class="text-lg font-bold">Setări și Securitate Card</h3>

                    <div class="space-y-4">
                        <!-- Freeze Toggle -->
                        <div class="flex items-center justify-between p-4 rounded-2xl bg-slate-900/80 border border-slate-800">
                            <div class="flex items-center gap-3">
                                <div class="w-10 h-10 rounded-xl bg-blue-500/10 text-blue-400 flex items-center justify-center">
                                    <i class="fa-solid fa-snowflake text-lg"></i>
                                </div>
                                <div>
                                    <p class="text-sm font-semibold">Blochează temporar cardul</p>
                                    <p class="text-xs text-slate-400">Oprește orice tranzacție nouă instant</p>
                                </div>
                            </div>
                            <label class="relative inline-flex items-center cursor-pointer">
                                <input type="checkbox" id="freeze-toggle" onchange="toggleFreezeCard()" class="sr-only peer">
                                <div class="w-11 h-6 bg-slate-700 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-slate-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-indigo-600"></div>
                            </label>
                        </div>

                        <!-- Reveal Details Toggle -->
                        <div class="flex items-center justify-between p-4 rounded-2xl bg-slate-900/80 border border-slate-800">
                            <div class="flex items-center gap-3">
                                <div class="w-10 h-10 rounded-xl bg-purple-500/10 text-purple-400 flex items-center justify-center">
                                    <i class="fa-solid fa-eye text-lg"></i>
                                </div>
                                <div>
                                    <p class="text-sm font-semibold">Afișează detaliile cardului</p>
                                    <p class="text-xs text-slate-400">Arată numărul complet și codul CVV</p>
                                </div>
                            </div>
                            <button onclick="toggleCardDetails()" id="btn-show-details" class="px-3 py-1.5 rounded-xl bg-slate-800 hover:bg-slate-700 text-xs font-semibold text-slate-200 transition-all border border-slate-700">
                                Afișează
                            </button>
                        </div>

                        <!-- Copy Card Number -->
                        <button onclick="copyCardNumber()" class="w-full flex items-center justify-between p-4 rounded-2xl bg-slate-900/80 border border-slate-800 hover:bg-slate-800/80 transition-all text-left">
                            <div class="flex items-center gap-3">
                                <div class="w-10 h-10 rounded-xl bg-emerald-500/10 text-emerald-400 flex items-center justify-center">
                                    <i class="fa-solid fa-copy text-lg"></i>
                                </div>
                                <div>
                                    <p class="text-sm font-semibold">Copiază Numărul Cardului</p>
                                    <p class="text-xs text-slate-400">Salvează în clipboard pentru cumpărături rapide</p>
                                </div>
                            </div>
                            <i class="fa-solid fa-chevron-right text-slate-500 text-xs"></i>
                        </button>
                    </div>
                </div>

            </div>
        </div>

        <!-- SECTION 3: ANALYTICS & BUDGETING -->
        <div id="tab-analytics" class="tab-content hidden space-y-6">
            <div>
                <h1 class="text-2xl md:text-3xl font-extrabold tracking-tight">Analiză Financiară</h1>
                <p class="text-slate-400 text-sm mt-1">Urmărește unde merg banii tăi în fiecare lună.</p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                <!-- Doughnut Chart Container -->
                <div class="glass-card rounded-3xl p-6 border border-slate-800 lg:col-span-1 flex flex-col items-center justify-center">
                    <h3 class="text-base font-bold mb-4 self-start">Categorii Cheltuieli</h3>
                    <div class="w-full max-w-[240px] relative">
                        <canvas id="spendingChart"></canvas>
                    </div>
                </div>

                <!-- Category Breakdown Bars -->
                <div class="glass-card rounded-3xl p-6 border border-slate-800 lg:col-span-2 space-y-5">
                    <h3 class="text-base font-bold">Detaliat pe Categorii (Luna Aceasta)</h3>
                    
                    <div id="category-bars-container" class="space-y-4">
                        <!-- Progress bars injected via JS -->
                    </div>
                </div>
            </div>
        </div>

        <!-- SECTION 4: CURRENCY EXCHANGE -->
        <div id="tab-exchange" class="tab-content hidden space-y-6">
            <div>
                <h1 class="text-2xl md:text-3xl font-extrabold tracking-tight">Schimb Valutar Instant</h1>
                <p class="text-slate-400 text-sm mt-1">Convertește bani între conturile tale la cursuri interbancare favorabile.</p>
            </div>

            <div class="max-w-xl mx-auto glass-card rounded-3xl p-6 md:p-8 border border-slate-800 space-y-6">
                
                <!-- From Currency Input -->
                <div class="space-y-2">
                    <label class="text-xs font-semibold text-slate-400">Vând (Din contul)</label>
                    <div class="flex items-center gap-3 bg-slate-900 p-3 rounded-2xl border border-slate-800">
                        <input type="number" id="exchange-from-amount" oninput="calculateExchange()" placeholder="0.00" value="100" class="w-full bg-transparent text-2xl font-bold text-white focus:outline-none">
                        <select id="exchange-from-curr" onchange="calculateExchange()" class="bg-slate-800 border border-slate-700 rounded-xl px-3 py-2 text-sm font-bold text-white focus:outline-none">
                            <option value="RON" selected>RON 🇷🇴</option>
                            <option value="EUR">EUR 🇪🇺</option>
                            <option value="USD">USD 🇺🇸</option>
                        </select>
                    </div>
                    <p id="exchange-from-balance" class="text-xs text-slate-500 text-right">Disponibil: 14.850,50 RON</p>
                </div>

                <!-- Switch Direction Button -->
                <div class="flex justify-center -my-2">
                    <button onclick="swapExchangeCurrencies()" class="w-10 h-10 rounded-full bg-indigo-600 hover:bg-indigo-500 text-white flex items-center justify-center shadow-lg transition-transform hover:rotate-180">
                        <i class="fa-solid fa-arrow-down-up-lock text-sm"></i>
                    </button>
                </div>

                <!-- To Currency Output -->
                <div class="space-y-2">
                    <label class="text-xs font-semibold text-slate-400">Cumpăr (În contul)</label>
                    <div class="flex items-center gap-3 bg-slate-900 p-3 rounded-2xl border border-slate-800">
                        <input type="number" id="exchange-to-amount" readonly placeholder="0.00" class="w-full bg-transparent text-2xl font-bold text-indigo-400 focus:outline-none">
                        <select id="exchange-to-curr" onchange="calculateExchange()" class="bg-slate-800 border border-slate-700 rounded-xl px-3 py-2 text-sm font-bold text-white focus:outline-none">
                            <option value="RON">RON 🇷🇴</option>
                            <option value="EUR" selected>EUR 🇪🇺</option>
                            <option value="USD">USD 🇺🇸</option>
                        </select>
                    </div>
                    <p id="exchange-rate-info" class="text-xs text-indigo-300 font-medium text-right">1 RON = 0.20 EUR</p>
                </div>

                <!-- Submit Exchange Button -->
                <button onclick="executeExchange()" class="w-full py-4 rounded-2xl bg-indigo-600 hover:bg-indigo-500 text-white font-bold text-sm transition-all shadow-lg shadow-indigo-600/30">
                    Efectuează Schimbul Valutar
                </button>
            </div>
        </div>

    </main>

    <!-- Mobile Bottom Navigation Bar -->
    <nav class="md:hidden fixed bottom-0 left-0 right-0 bg-slate-900/95 border-t border-slate-800 backdrop-blur-lg z-40 flex justify-around p-2">
        <button onclick="switchTab('dashboard')" id="mobile-nav-dashboard" class="flex flex-col items-center gap-1 p-2 text-brand-500">
            <i class="fa-solid fa-chart-pie text-lg"></i>
            <span class="text-[10px] font-medium">Panou</span>
        </button>
        <button onclick="switchTab('cards')" id="mobile-nav-cards" class="flex flex-col items-center gap-1 p-2 text-slate-400">
            <i class="fa-solid fa-credit-card text-lg"></i>
            <span class="text-[10px] font-medium">Carduri</span>
        </button>
        <button onclick="switchTab('analytics')" id="mobile-nav-analytics" class="flex flex-col items-center gap-1 p-2 text-slate-400">
            <i class="fa-solid fa-chart-line text-lg"></i>
            <span class="text-[10px] font-medium">Analiză</span>
        </button>
        <button onclick="switchTab('exchange')" id="mobile-nav-exchange" class="flex flex-col items-center gap-1 p-2 text-slate-400">
            <i class="fa-solid fa-right-left text-lg"></i>
            <span class="text-[10px] font-medium">Schimb</span>
        </button>
    </nav>

    <!-- MODAL 1: SEND / PAY MONEY -->
    <div id="modal-send" class="fixed inset-0 bg-slate-950/80 backdrop-blur-md z-50 flex items-center justify-center p-4 hidden">
        <div class="glass-card bg-slate-900 rounded-3xl max-w-md w-full p-6 border border-slate-800 space-y-5 animate-in fade-in zoom-in duration-200">
            <div class="flex justify-between items-center">
                <h3 class="text-lg font-bold">Trimite Bani</h3>
                <button onclick="closeModal('modal-send')" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>

            <div class="space-y-4">
                <div>
                    <label class="text-xs font-semibold text-slate-400 mb-1 block">Nume Destinatar / IBAN</label>
                    <input type="text" id="send-recipient" placeholder="ex: Andrei Ionescu sau RO49VOLT..." class="w-full bg-slate-950 border border-slate-700 rounded-xl p-3 text-sm focus:outline-none focus:border-indigo-500">
                </div>

                <div>
                    <label class="text-xs font-semibold text-slate-400 mb-1 block">Suma de trimis</label>
                    <div class="flex gap-2">
                        <input type="number" id="send-amount" placeholder="0.00" class="w-full bg-slate-950 border border-slate-700 rounded-xl p-3 text-sm focus:outline-none focus:border-indigo-500">
                        <select id="send-currency" class="bg-slate-800 border border-slate-700 rounded-xl px-3 text-sm font-bold">
                            <option value="RON">RON</option>
                            <option value="EUR">EUR</option>
                            <option value="USD">USD</option>
                        </select>
                    </div>
                </div>

                <div>
                    <label class="text-xs font-semibold text-slate-400 mb-1 block">Categorie Tranzacție</label>
                    <select id="send-category" class="w-full bg-slate-950 border border-slate-700 rounded-xl p-3 text-sm focus:outline-none focus:border-indigo-500">
                        <option value="Transfer">Transfer Persoane</option>
                        <option value="Shopping">Shopping</option>
                        <option value="Mâncare & Băuturi">Mâncare & Băuturi</option>
                        <option value="Abonamente">Abonamente</option>
                    </select>
                </div>
            </div>

            <div class="flex gap-3 pt-2">
                <button onclick="closeModal('modal-send')" class="flex-1 py-3 rounded-xl bg-slate-800 text-slate-300 hover:bg-slate-700 font-semibold text-xs">Anulează</button>
                <button onclick="executeSendMoney()" class="flex-1 py-3 rounded-xl bg-indigo-600 hover:bg-indigo-500 text-white font-semibold text-xs">Confirmă Plata</button>
            </div>
        </div>
    </div>

    <!-- MODAL 2: TOP UP (ADD MONEY) -->
    <div id="modal-topup" class="fixed inset-0 bg-slate-950/80 backdrop-blur-md z-50 flex items-center justify-center p-4 hidden">
        <div class="glass-card bg-slate-900 rounded-3xl max-w-md w-full p-6 border border-slate-800 space-y-5">
            <div class="flex justify-between items-center">
                <h3 class="text-lg font-bold">Alimentează Contul</h3>
                <button onclick="closeModal('modal-topup')" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>

            <div class="space-y-4">
                <div>
                    <label class="text-xs font-semibold text-slate-400 mb-1 block">Metodă de Alimentare</label>
                    <div class="grid grid-cols-2 gap-3">
                        <button class="p-3 rounded-xl border border-indigo-500 bg-indigo-500/10 flex items-center justify-center gap-2 text-xs font-bold text-indigo-300">
                            <i class="fa-brands fa-apple text-sm"></i> Apple Pay
                        </button>
                        <button class="p-3 rounded-xl border border-slate-700 bg-slate-800 hover:bg-slate-700 flex items-center justify-center gap-2 text-xs font-bold text-slate-300">
                            <i class="fa-solid fa-credit-card text-sm"></i> Card Bancar
                        </button>
                    </div>
                </div>

                <div>
                    <label class="text-xs font-semibold text-slate-400 mb-1 block">Suma adăugată</label>
                    <div class="flex gap-2">
                        <input type="number" id="topup-amount" placeholder="500.00" class="w-full bg-slate-950 border border-slate-700 rounded-xl p-3 text-sm focus:outline-none focus:border-indigo-500">
                        <select id="topup-currency" class="bg-slate-800 border border-slate-700 rounded-xl px-3 text-sm font-bold">
                            <option value="RON">RON</option>
                            <option value="EUR">EUR</option>
                            <option value="USD">USD</option>
                        </select>
                    </div>
                </div>
            </div>

            <div class="flex gap-3 pt-2">
                <button onclick="closeModal('modal-topup')" class="flex-1 py-3 rounded-xl bg-slate-800 text-slate-300 hover:bg-slate-700 font-semibold text-xs">Anulează</button>
                <button onclick="executeTopUp()" class="flex-1 py-3 rounded-xl bg-emerald-600 hover:bg-emerald-500 text-white font-semibold text-xs">Adaugă Fonduri</button>
            </div>
        </div>
    </div>

    <!-- APPLICATION JAVASCRIPT LOGIC -->
    <script>
        // State Management
        let appState = {
            activeCurrency: 'RON',
            isCardFrozen: false,
            areCardDetailsVisible: false,
            balances: {
                RON: 14850.50,
                EUR: 6000.00,
                USD: 850.00
            },
            exchangeRates: {
                RON: { EUR: 0.201, USD: 0.218, RON: 1 },
                EUR: { RON: 4.975, USD: 1.085, EUR: 1 },
                USD: { RON: 4.582, EUR: 0.921, USD: 1 }
            },
            transactions: [
                { id: 1, name: "Mega Image Băneasa", category: "Mâncare & Băuturi", amount: -84.50, currency: "RON", icon: "fa-basket-shopping", date: "Astăzi, 14:20" },
                { id: 2, name: "Alimentare Apple Pay", category: "Salariu", amount: +500.00, currency: "RON", icon: "fa-wallet", date: "Astăzi, 09:15" },
                { id: 3, name: "Abonament Netflix", category: "Abonamente", amount: -11.99, currency: "EUR", icon: "fa-film", date: "Ieri, 22:00" },
                { id: 4, name: "Zara Fashion SRL", category: "Shopping", amount: -249.90, currency: "RON", icon: "fa-bag-shopping", date: "12 Oct" },
                { id: 5, name: "Transfer de la Mihai D.", category: "Transfer", amount: +150.00, currency: "RON", icon: "fa-arrow-down-left", date: "10 Oct" },
                { id: 6, name: "Starbucks Unirii", category: "Mâncare & Băuturi", amount: -26.00, currency: "RON", icon: "fa-mug-hot", date: "09 Oct" }
            ]
        };

        let spendingChartInstance = null;

        // Window Initialization
        window.onload = function() {
            updateBalanceDisplays();
            renderTransactions();
            initChart();
            calculateExchange();
        };

        // Switch Tabs Logic
        function switchTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.getElementById(`tab-${tabId}`).classList.remove('hidden');

            // Update Nav styles desktop
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('text-brand-500', 'bg-indigo-500/10', 'border', 'border-indigo-500/20');
                btn.classList.add('text-slate-400');
            });
            const activeNav = document.getElementById(`nav-${tabId}`);
            if (activeNav) {
                activeNav.classList.add('text-brand-500', 'bg-indigo-500/10', 'border', 'border-indigo-500/20');
                activeNav.classList.remove('text-slate-400');
            }

            // Update Nav styles mobile
            document.querySelectorAll('nav.md\\:hidden button').forEach(btn => {
                btn.classList.remove('text-brand-500');
                btn.classList.add('text-slate-400');
            });
            const activeMobileNav = document.getElementById(`mobile-nav-${tabId}`);
            if (activeMobileNav) {
                activeMobileNav.classList.add('text-brand-500');
                activeMobileNav.classList.remove('text-slate-400');
            }

            if(tabId === 'analytics') {
                setTimeout(updateChart, 100);
            }
        }

        // Change Active Currency
        function changeCurrency(curr) {
            appState.activeCurrency = curr;
            document.querySelectorAll('.curr-tab-btn').forEach(btn => {
                btn.classList.remove('bg-brand-500', 'text-white', 'shadow-lg', 'shadow-indigo-500/25');
                btn.classList.add('text-slate-400');
            });
            const activeBtn = document.getElementById(`curr-btn-${curr}`);
            if (activeBtn) {
                activeBtn.classList.add('bg-brand-500', 'text-white', 'shadow-lg', 'shadow-indigo-500/25');
                activeBtn.classList.remove('text-slate-400');
            }

            document.getElementById('active-currency-label').innerText = curr;
            document.getElementById('main-currency-symbol').innerText = curr;
            updateBalanceDisplays();
        }

        // Update Balance Labels across UI
        function updateBalanceDisplays() {
            const curr = appState.activeCurrency;
            const bal = appState.balances[curr];
            document.getElementById('main-balance-display').innerText = formatMoney(bal);

            document.getElementById('vault-ron-val').innerText = `${formatMoney(appState.balances.RON)} RON`;
            document.getElementById('vault-eur-val').innerText = `${formatMoney(appState.balances.EUR)} EUR`;
            document.getElementById('vault-usd-val').innerText = `${formatMoney(appState.balances.USD)} USD`;

            // Update Exchange From Balance
            const fromCurr = document.getElementById('exchange-from-curr').value;
            document.getElementById('exchange-from-balance').innerText = `Disponibil: ${formatMoney(appState.balances[fromCurr])} ${fromCurr}`;
        }

        // Format Number to Currency Format
        function formatMoney(amount) {
            return new Intl.NumberFormat('ro-RO', { minimumFractionDigits: 2, maximumFractionDigits: 2 }).format(amount);
        }

        // Render Transactions List
        function renderTransactions() {
            const container = document.getElementById('transactions-list');
            const searchVal = document.getElementById('tx-search').value.toLowerCase();
            const catVal = document.getElementById('tx-category-filter').value;

            container.innerHTML = '';

            const filtered = appState.transactions.filter(tx => {
                const matchesSearch = tx.name.toLowerCase().includes(searchVal);
                const matchesCat = catVal === 'ALL' || tx.category === catVal;
                return matchesSearch && matchesCat;
            });

            if (filtered.length === 0) {
                container.innerHTML = `<div class="text-center py-8 text-slate-500 text-xs">Nicio tranzacție găsită</div>`;
                return;
            }

            filtered.forEach(tx => {
                const isPositive = tx.amount > 0;
                const amountClass = isPositive ? 'text-emerald-400' : 'text-slate-200';
                const sign = isPositive ? '+' : '';

                const itemHtml = `
                    <div class="flex items-center justify-between p-3 rounded-2xl bg-slate-900/50 hover:bg-slate-800/60 border border-slate-800/50 transition-all">
                        <div class="flex items-center gap-3">
                            <div class="w-10 h-10 rounded-xl bg-slate-800 flex items-center justify-center text-slate-300 border border-slate-700/50">
                                <i class="fa-solid ${tx.icon}"></i>
                            </div>
                            <div>
                                <p class="text-sm font-semibold text-white">${tx.name}</p>
                                <div class="flex items-center gap-2 text-[11px] text-slate-400">
                                    <span>${tx.category}</span>
                                    <span>•</span>
                                    <span>${tx.date}</span>
                                </div>
                            </div>
                        </div>
                        <div class="text-right">
                            <p class="text-sm font-bold ${amountClass}">${sign}${formatMoney(tx.amount)} ${tx.currency}</p>
                            <span class="text-[10px] text-slate-500">Completat</span>
                        </div>
                    </div>
                `;
                container.innerHTML += itemHtml;
            });
        }

        // Modals Management
        function openModal(id) {
            document.getElementById(id).classList.remove('hidden');
        }

        function closeModal(id) {
            document.getElementById(id).classList.add('hidden');
        }

        // Toast Notification System
        function showToast(message, type = 'success') {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            
            const bgClass = type === 'success' ? 'bg-emerald-950/90 border-emerald-500/50 text-emerald-200' : 'bg-rose-950/90 border-rose-500/50 text-rose-200';
            const icon = type === 'success' ? 'fa-circle-check' : 'fa-circle-exclamation';

            toast.className = `glass-card p-4 rounded-2xl border ${bgClass} shadow-xl flex items-center gap-3 pointer-events-auto transition-all transform duration-300 translate-y-2`;
            toast.innerHTML = `
                <i class="fa-solid ${icon} text-lg"></i>
                <span class="text-xs font-semibold">${message}</span>
            `;

            container.appendChild(toast);

            setTimeout(() => {
                toast.classList.add('opacity-0', '-translate-y-2');
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        // Action: Execute Money Transfer
        function executeSendMoney() {
            const recipient = document.getElementById('send-recipient').value;
            const amount = parseFloat(document.getElementById('send-amount').value);
            const currency = document.getElementById('send-currency').value;
            const category = document.getElementById('send-category').value;

            if (!recipient || isNaN(amount) || amount <= 0) {
                showToast('Te rugăm să introduci date valide.', 'error');
                return;
            }

            if (appState.balances[currency] < amount) {
                showToast('Fonduri insuficiente în acest cont!', 'error');
                return;
            }

            if (appState.isCardFrozen) {
                showToast('Contul/Cardul este blocat temporar.', 'error');
                return;
            }

            appState.balances[currency] -= amount;
            
            // Add transaction
            appState.transactions.unshift({
                id: Date.now(),
                name: `Către ${recipient}`,
                category: category,
                amount: -amount,
                currency: currency,
                icon: "fa-paper-plane",
                date: "Acum"
            });

            updateBalanceDisplays();
            renderTransactions();
            updateChart();
            closeModal('modal-send');
            showToast(`Ai trimis cu succes ${formatMoney(amount)} ${currency} către ${recipient}!`);

            // Reset Form
            document.getElementById('send-recipient').value = '';
            document.getElementById('send-amount').value = '';
        }

        // Action: Execute Top Up
        function executeTopUp() {
            const amount = parseFloat(document.getElementById('topup-amount').value);
            const currency = document.getElementById('topup-currency').value;

            if (isNaN(amount) || amount <= 0) {
                showToast('Introdu o sumă validă.', 'error');
                return;
            }

            appState.balances[currency] += amount;

            appState.transactions.unshift({
                id: Date.now(),
                name: "Alimentare Cont",
                category: "Salariu",
                amount: +amount,
                currency: currency,
                icon: "fa-wallet",
                date: "Acum"
            });

            updateBalanceDisplays();
            renderTransactions();
            closeModal('modal-topup');
            showToast(`S-au adăugat ${formatMoney(amount)} ${currency} în contul tău.`);

            document.getElementById('topup-amount').value = '';
        }

        // Exchange Calculation Logic
        function calculateExchange() {
            const fromCurr = document.getElementById('exchange-from-curr').value;
            const toCurr = document.getElementById('exchange-to-curr').value;
            const fromAmt = parseFloat(document.getElementById('exchange-from-amount').value) || 0;

            const rate = appState.exchangeRates[fromCurr][toCurr];
            const result = fromAmt * rate;

            document.getElementById('exchange-to-amount').value = result.toFixed(2);
            document.getElementById('exchange-rate-info').innerText = `1 ${fromCurr} = ${rate.toFixed(4)} ${toCurr}`;
            document.getElementById('exchange-from-balance').innerText = `Disponibil: ${formatMoney(appState.balances[fromCurr])} ${fromCurr}`;
        }

        function swapExchangeCurrencies() {
            const fromSelect = document.getElementById('exchange-from-curr');
            const toSelect = document.getElementById('exchange-to-curr');
            const temp = fromSelect.value;
            fromSelect.value = toSelect.value;
            toSelect.value = temp;
            calculateExchange();
        }

        function executeExchange() {
            const fromCurr = document.getElementById('exchange-from-curr').value;
            const toCurr = document.getElementById('exchange-to-curr').value;
            const fromAmt = parseFloat(document.getElementById('exchange-from-amount').value);

            if (fromCurr === toCurr) {
                showToast('Alege monede diferite pentru schimb.', 'error');
                return;
            }

            if (isNaN(fromAmt) || fromAmt <= 0) {
                showToast('Suma introdusă este invalidă.', 'error');
                return;
            }

            if (appState.balances[fromCurr] < fromAmt) {
                showToast('Fonduri insuficiente pentru schimb valutar.', 'error');
                return;
            }

            const rate = appState.exchangeRates[fromCurr][toCurr];
            const toAmt = fromAmt * rate;

            appState.balances[fromCurr] -= fromAmt;
            appState.balances[toCurr] += toAmt;

            appState.transactions.unshift({
                id: Date.now(),
                name: `Schimb Valutar (${fromCurr} ➔ ${toCurr})`,
                category: "Transfer",
                amount: -fromAmt,
                currency: fromCurr,
                icon: "fa-arrows-rotate",
                date: "Acum"
            });

            updateBalanceDisplays();
            renderTransactions();
            showToast(`Schimb efectuat: ${formatMoney(fromAmt)} ${fromCurr} ➔ ${formatMoney(toAmt)} ${toCurr}`);
        }

        // Virtual Card Actions
        function flipCard() {
            document.getElementById('card-element').classList.toggle('card-flipped');
        }

        function toggleFreezeCard() {
            appState.isCardFrozen = document.getElementById('freeze-toggle').checked;
            const cardEl = document.getElementById('card-element');
            if (appState.isCardFrozen) {
                cardEl.classList.add('opacity-50', 'grayscale');
                showToast('Cardul tău virtual a fost blocat.', 'error');
            } else {
                cardEl.classList.remove('opacity-50', 'grayscale');
                showToast('Cardul tău este activ.');
            }
        }

        function toggleCardDetails() {
            appState.areCardDetailsVisible = !appState.areCardDetailsVisible;
            const numDisp = document.getElementById('card-number-display');
            const cvvDisp = document.getElementById('card-cvv-display');
            const btn = document.getElementById('btn-show-details');

            if (appState.areCardDetailsVisible) {
                numDisp.innerText = '4532 8912 3456 8842';
                cvvDisp.innerText = '849';
                btn.innerText = 'Ascunde';
            } else {
                numDisp.innerText = '•••• •••• •••• 8842';
                cvvDisp.innerText = '•••';
                btn.innerText = 'Afișează';
            }
        }

        function copyCardNumber() {
            // Copy mock card number fallback using prompt or clipboard execCommand
            const dummy = document.createElement('input');
            document.body.appendChild(dummy);
            dummy.value = '4532891234568842';
            dummy.select();
            document.execCommand('copy');
            document.body.removeChild(dummy);
            showToast('Numărul de card a fost copiat în clipboard!');
        }

        // Theme Toggle (Dark/Light)
        function toggleTheme() {
            const html = document.documentElement;
            const status = document.getElementById('theme-status');
            if (html.classList.contains('dark')) {
                html.classList.remove('dark');
                status.innerText = 'INACTIV';
            } else {
                html.classList.add('dark');
                status.innerText = 'ACTIV';
            }
        }

        // Chart.js & Analytics Rendering
        function initChart() {
            const ctx = document.getElementById('spendingChart').getContext('2d');
            spendingChartInstance = new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: [],
                    datasets: [{
                        data: [],
                        backgroundColor: ['#6366f1', '#10b981', '#f59e0b', '#ec4899', '#8b5cf6'],
                        borderWidth: 0
                    }]
                },
                options: {
                    responsive: true,
                    plugins: {
                        legend: { display: false }
                    },
                    cutout: '75%'
                }
            });
            updateChart();
        }

        function updateChart() {
            // Calculate totals per category from expense transactions
            const categories = {};
            appState.transactions.forEach(tx => {
                if (tx.amount < 0) {
                    const cat = tx.category;
                    const val = Math.abs(tx.amount);
                    categories[cat] = (categories[cat] || 0) + val;
                }
            });

            const labels = Object.keys(categories);
            const data = Object.values(categories);

            if (spendingChartInstance) {
                spendingChartInstance.data.labels = labels;
                spendingChartInstance.data.datasets[0].data = data;
                spendingChartInstance.update();
            }

            // Render category breakdown progress bars
            const barsContainer = document.getElementById('category-bars-container');
            barsContainer.innerHTML = '';

            const totalSpent = data.reduce((a, b) => a + b, 0) || 1;

            labels.forEach((cat, idx) => {
                const amount = categories[cat];
                const pct = Math.round((amount / totalSpent) * 100);
                const colors = ['bg-indigo-500', 'bg-emerald-500', 'bg-amber-500', 'bg-pink-500', 'bg-purple-500'];

                barsContainer.innerHTML += `
                    <div class="space-y-1">
                        <div class="flex justify-between text-xs font-semibold">
                            <span class="text-slate-300">${cat}</span>
                            <span class="text-slate-400">${formatMoney(amount)} RON (${pct}%)</span>
                        </div>
                        <div class="w-full h-2 rounded-full bg-slate-800 overflow-hidden">
                            <div class="h-full ${colors[idx % colors.length]} transition-all duration-500" style="width: ${pct}%"></div>
                        </div>
                    </div>
                `;
            });
        }
    </script>
</body>
</html>
