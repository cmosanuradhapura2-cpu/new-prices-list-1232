<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>C MOS Computers & Technologies | Product & CCTV Catalog</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                    colors: {
                        cmos: {
                            50: '#fffbe6',
                            400: '#f59e0b',
                            500: '#d97706',
                            600: '#b45309',
                            cyan: '#06b6d4',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        .custom-scrollbar::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        .custom-scrollbar::-webkit-scrollbar-track {
            background: #0f172a;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: #334155;
            border-radius: 3px;
        }
    </style>
</head>
<body class="bg-slate-950 text-slate-100 font-sans min-h-screen flex flex-col antialiased">

    <!-- Top Contact & Branch Banner -->
    <div class="bg-gradient-to-r from-amber-600 via-amber-700 to-slate-900 text-slate-100 px-4 py-2 text-xs border-b border-amber-500/30">
        <div class="max-w-7xl mx-auto flex flex-col sm:flex-row justify-between items-center gap-2">
            <div class="flex items-center space-x-2 font-medium">
                <i class="fa-solid fa-location-dot text-amber-300"></i>
                <span>New Bus Stand, Anuradhapura</span>
                <span class="hidden md:inline text-amber-300/60">|</span>
                <span class="hidden md:inline text-amber-200">Authorized CCTV & Computer Solutions</span>
            </div>
            <div class="flex items-center space-x-4">
                <a href="tel:0703182015" class="hover:text-amber-200 font-semibold flex items-center gap-1.5">
                    <i class="fa-solid fa-phone text-amber-300"></i> 070 318 2015
                </a>
                <span class="text-slate-500">/</span>
                <a href="tel:0252228715" class="hover:text-amber-200 font-semibold hidden sm:inline">025 222 8715</a>
                <span class="text-slate-500 hidden sm:inline">/</span>
                <a href="tel:0713182015" class="hover:text-amber-200 font-semibold hidden sm:inline">071 318 2015</a>
            </div>
        </div>
    </div>

    <!-- Main Navigation Header -->
    <header class="sticky top-0 z-30 bg-slate-900/95 backdrop-blur-md border-b border-slate-800 shadow-xl">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between gap-4">
            
            <!-- Logo & Store Name -->
            <div class="flex items-center space-x-3 cursor-pointer" onclick="resetFilters()">
                <div class="w-11 h-11 rounded-xl bg-gradient-to-tr from-amber-500 to-cyan-500 flex items-center justify-center text-slate-950 font-black text-xl shadow-lg shadow-amber-500/20">
                    <i class="fa-solid fa-microchip"></i>
                </div>
                <div>
                    <h1 class="text-lg sm:text-xl font-extrabold bg-gradient-to-r from-amber-400 via-white to-cyan-400 bg-clip-text text-transparent leading-none">
                        C MOS COMPUTERS
                    </h1>
                    <p class="text-[11px] text-slate-400 font-medium tracking-wide mt-1">
                        & TECHNOLOGIES <span class="text-amber-400 font-bold ml-1">• ANURADHAPURA</span>
                    </p>
                </div>
            </div>

            <!-- Global Live Search -->
            <div class="flex-1 max-w-md hidden lg:block">
                <div class="relative">
                    <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
                    <input type="text" id="searchInput" oninput="handleSearch(this.value)" placeholder="Search Dahua, Hikvision, SSDs, Laptops, 4G Routers..." 
                        class="w-full pl-10 pr-4 py-2 bg-slate-950 border border-slate-700/80 rounded-xl text-slate-200 placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-amber-500 text-sm transition-all">
                </div>
            </div>

            <!-- Action Controls -->
            <div class="flex items-center space-x-2 sm:space-x-3">
                <!-- Sync Status / Firebase Settings Indicator -->
                <button onclick="openFirebaseSettingsModal()" id="dbStatusBadge" title="Cloud Sync Settings"
                    class="px-2.5 py-1.5 rounded-xl bg-slate-800 hover:bg-slate-700 text-amber-400 border border-amber-500/30 text-xs font-semibold flex items-center space-x-1.5 transition">
                    <i class="fa-solid fa-cloud text-xs"></i>
                    <span id="syncModeText" class="hidden sm:inline">Local Storage</span>
                </button>

                <!-- Customer / Wholesale View Mode Toggle -->
                <button onclick="toggleViewMode()" id="viewModeBtn" title="Toggle Wholesale / Customer View"
                    class="px-3 py-2 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs font-semibold border border-slate-700 flex items-center space-x-2 transition">
                    <i class="fa-solid fa-shield-halved text-amber-400" id="viewModeIcon"></i>
                    <span id="viewModeLabel" class="hidden sm:inline">Admin View</span>
                </button>

                <!-- Add New Product Button (Admin Only or Default Visible) -->
                <button onclick="openProductModal()" id="addProductBtn"
                    class="px-3.5 py-2 rounded-xl bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-400 hover:to-amber-500 text-slate-950 font-bold text-xs sm:text-sm shadow-md shadow-amber-500/20 flex items-center space-x-1.5 transition">
                    <i class="fa-solid fa-plus text-xs"></i>
                    <span>Add Item</span>
                </button>
            </div>
        </div>

        <!-- Mobile Search Input -->
        <div class="p-3 bg-slate-900 border-t border-slate-800 lg:hidden">
            <div class="relative">
                <i class="fa-solid fa-magnifying-glass absolute left-3 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
                <input type="text" oninput="handleSearch(this.value)" placeholder="Search products, models, prices..." 
                    class="w-full pl-9 pr-4 py-2 bg-slate-950 border border-slate-700 rounded-lg text-slate-200 placeholder-slate-400 text-sm">
            </div>
        </div>
    </header>

    <!-- App Layout Body -->
    <main class="flex-1 max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-6 flex flex-col md:flex-row gap-6">

        <!-- Sidebar Category Navigation -->
        <aside class="w-full md:w-64 flex-shrink-0 space-y-5">

            <!-- CCTV Security Brands Card -->
            <div class="bg-slate-900/90 rounded-2xl p-4 border border-slate-800 shadow-xl">
                <div class="flex items-center space-x-2 mb-3 px-1 text-amber-400">
                    <i class="fa-solid fa-video"></i>
                    <h2 class="text-xs font-extrabold uppercase tracking-wider">CCTV Cameras & Brands</h2>
                </div>
                <div class="space-y-1" id="cctvBrandFilters">
                    <!-- CCTV Brand filters injected dynamically -->
                </div>
            </div>

            <!-- Computer Hardware & Accessories Card -->
            <div class="bg-slate-900/90 rounded-2xl p-4 border border-slate-800 shadow-xl">
                <div class="flex items-center space-x-2 mb-3 px-1 text-cyan-400">
                    <i class="fa-solid fa-desktop"></i>
                    <h2 class="text-xs font-extrabold uppercase tracking-wider">Computer Hardware</h2>
                </div>
                <div class="space-y-1" id="generalCatFilters">
                    <!-- General Category filters injected dynamically -->
                </div>
            </div>

            <!-- Branch Contact Quick-Card -->
            <div class="bg-gradient-to-br from-slate-900 to-slate-900/80 rounded-2xl p-4 border border-slate-800 text-xs space-y-2 text-slate-300">
                <div class="font-bold text-amber-400 flex items-center space-x-1.5">
                    <i class="fa-solid fa-store"></i>
                    <span>C MOS Store Details</span>
                </div>
                <p class="text-[11px] text-slate-400 leading-relaxed">Visit our store at New Bus Stand, Anuradhapura for retail, wholesale & technician discounts.</p>
                <div class="pt-2 border-t border-slate-800 text-[11px] space-y-1 font-mono text-slate-300">
                    <div><i class="fa-brands fa-whatsapp text-emerald-400 w-4"></i> 070 318 2015</div>
                    <div><i class="fa-solid fa-phone text-sky-400 w-4"></i> 025 222 8715</div>
                </div>
            </div>
        </aside>

        <!-- Product Inventory Content Area -->
        <section class="flex-1 flex flex-col space-y-4">

            <!-- Control Bar & Filter Breadcrumb -->
            <div class="bg-slate-900/90 rounded-2xl p-4 border border-slate-800 flex flex-wrap items-center justify-between gap-3 shadow-md">
                <div>
                    <h2 id="currentCategoryTitle" class="text-base sm:text-lg font-bold text-white flex items-center space-x-2">
                        <span>All Inventory</span>
                    </h2>
                    <p id="productCountSub" class="text-xs text-slate-400">Loading catalog items...</p>
                </div>

                <div class="flex items-center space-x-3">
                    <!-- Sort Selection -->
                    <div class="flex items-center space-x-2">
                        <label class="text-xs text-slate-400 hidden sm:inline">Sort:</label>
                        <select id="sortSelect" onchange="handleSort(this.value)" class="bg-slate-950 border border-slate-700 rounded-xl px-2.5 py-1.5 text-xs text-slate-300 focus:outline-none focus:ring-1 focus:ring-amber-500">
                            <option value="default">Featured</option>
                            <option value="price-low">Price: Low to High</option>
                            <option value="price-high">Price: High to Low</option>
                            <option value="warranty">Warranty Period</option>
                            <option value="stock">In Stock First</option>
                        </select>
                    </div>
                </div>
            </div>

            <!-- Product Cards Grid -->
            <div id="productGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
                <!-- Products dynamically rendered here -->
            </div>

            <!-- Empty Search Results State -->
            <div id="emptyState" class="hidden flex-col items-center justify-center py-16 px-4 bg-slate-900/50 rounded-2xl border border-dashed border-slate-800 text-center">
                <div class="w-16 h-16 rounded-full bg-slate-800 flex items-center justify-center text-slate-500 mb-3 text-2xl">
                    <i class="fa-solid fa-box-open"></i>
                </div>
                <h3 class="text-base font-semibold text-slate-200">No matching products found</h3>
                <p class="text-xs text-slate-400 max-w-xs mt-1">Try clearing your search terms or choosing a different CCTV brand/category.</p>
                <button onclick="resetFilters()" class="mt-4 px-4 py-2 text-xs bg-slate-800 hover:bg-slate-700 border border-slate-700 rounded-xl text-amber-400 font-semibold transition">
                    Reset Filters
                </button>
            </div>
        </section>

    </main>

    <!-- Product Add/Edit Modal Form -->
    <div id="productModal" class="fixed inset-0 bg-slate-950/80 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-slate-900 border border-slate-700 rounded-2xl w-full max-w-lg overflow-hidden shadow-2xl">
            
            <div class="bg-slate-800/90 px-6 py-4 border-b border-slate-700 flex justify-between items-center">
                <h3 id="modalTitle" class="text-base font-bold text-amber-400 flex items-center gap-2">
                    <i class="fa-solid fa-box"></i> <span>Add New Inventory Item</span>
                </h3>
                <button onclick="closeProductModal()" class="text-slate-400 hover:text-white text-lg">
                    <i class="fa-solid fa-xmark"></i>
                </button>
            </div>

            <form id="productForm" onsubmit="saveProduct(event)" class="p-6 space-y-4 max-h-[80vh] overflow-y-auto custom-scrollbar">
                <input type="hidden" id="prodId">

                <!-- Title -->
                <div>
                    <label class="block text-xs font-semibold text-slate-300 mb-1">Product Title *</label>
                    <input type="text" id="prodTitle" required placeholder="e.g. Dahua 2MP Full-Color Bullet Camera" 
                        class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-sm text-slate-100 focus:outline-none focus:ring-2 focus:ring-amber-500">
                </div>

                <!-- Main Category & CCTV Brand -->
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-semibold text-slate-300 mb-1">Category *</label>
                        <select id="prodCategory" required onchange="handleModalCategoryChange(this.value)" 
                            class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-sm text-slate-100 focus:outline-none focus:ring-2 focus:ring-amber-500">
                            <option value="CCTV Security">CCTV Security</option>
                            <option value="Laptops & Desktops">Laptops & Desktops</option>
                            <option value="Monitors">Monitors (19" - 27")</option>
                            <option value="Storage & SSDs">Storage & SSDs</option>
                            <option value="Networking & 4G">Networking & 4G SIM</option>
                            <option value="Power & UPS">Power & UPS</option>
                            <option value="Peripherals">Peripherals & Gaming</option>
                            <option value="CCTV Accessories">CCTV Accessories</option>
                            <option value="Services & Repair">Services & Repair</option>
                        </select>
                    </div>

                    <div>
                        <label class="block text-xs font-semibold text-slate-300 mb-1">CCTV Brand</label>
                        <select id="prodCctvBrand" 
                            class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-sm text-slate-100 focus:outline-none focus:ring-2 focus:ring-amber-500">
                            <option value="None">None (N/A)</option>
                            <option value="Dahua">Dahua</option>
                            <option value="Hikvision">Hikvision</option>
                            <option value="Ezviz">Ezviz</option>
                            <option value="Tiandy">Tiandy</option>
                            <option value="Imou">Imou</option>
                            <option value="Chinese CCTV">Chinese CCTV</option>
                        </select>
                    </div>
                </div>

                <!-- Retail & Wholesale Prices (LKR) -->
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-semibold text-slate-300 mb-1">Retail Price (LKR) *</label>
                        <input type="number" step="0.01" id="prodRetailPrice" required placeholder="8500.00" 
                            class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-sm text-slate-100 focus:outline-none focus:ring-2 focus:ring-amber-500">
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-slate-300 mb-1">Wholesale Price (LKR) *</label>
                        <input type="number" step="0.01" id="prodWholesalePrice" required placeholder="7200.00" 
                            class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-sm text-slate-100 focus:outline-none focus:ring-2 focus:ring-amber-500">
                    </div>
                </div>

                <!-- Warranty & Stock Status -->
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-semibold text-slate-300 mb-1">Warranty Period *</label>
                        <select id="prodWarranty" required
                            class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-sm text-slate-100 focus:outline-none focus:ring-2 focus:ring-amber-500">
                            <option value="No Warranty">No Warranty</option>
                            <option value="6 Months">6 Months</option>
                            <option value="1 Year">1 Year</option>
                            <option value="2 Years">2 Years</option>
                            <option value="3 Years">3 Years</option>
                        </select>
                    </div>

                    <div>
                        <label class="block text-xs font-semibold text-slate-300 mb-1">Stock Availability *</label>
                        <select id="prodStock" required
                            class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-sm text-slate-100 focus:outline-none focus:ring-2 focus:ring-amber-500">
                            <option value="In Stock">In Stock</option>
                            <option value="Limited Stock">Limited Stock</option>
                            <option value="Out of Stock">Out of Stock</option>
                        </select>
                    </div>
                </div>

                <!-- Model Number / Part Code -->
                <div>
                    <label class="block text-xs font-semibold text-slate-300 mb-1">Model / Part Code</label>
                    <input type="text" id="prodModel" placeholder="e.g. DH-HAC-HDW1239TLP" 
                        class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-sm text-slate-100 focus:outline-none focus:ring-2 focus:ring-amber-500">
                </div>

                <!-- Image URL -->
                <div>
                    <label class="block text-xs font-semibold text-slate-300 mb-1">Image URL (Optional)</label>
                    <input type="url" id="prodImage" placeholder="https://images.unsplash.com/..." 
                        class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-sm text-slate-100 focus:outline-none focus:ring-2 focus:ring-amber-500">
                </div>

                <!-- Specs / Key Notes -->
                <div>
                    <label class="block text-xs font-semibold text-slate-300 mb-1">Key Specifications / Specs</label>
                    <textarea id="prodDesc" rows="2" placeholder="24/7 Full Color, 3.6mm Lens, Built-in Mic..." 
                        class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-sm text-slate-100 focus:outline-none focus:ring-2 focus:ring-amber-500"></textarea>
                </div>

                <!-- Form Action Buttons -->
                <div class="pt-3 flex justify-end space-x-3 border-t border-slate-800">
                    <button type="button" onclick="closeProductModal()" 
                        class="px-4 py-2 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-300 text-xs font-semibold border border-slate-700">Cancel</button>
                    <button type="submit" 
                        class="px-5 py-2 rounded-xl bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-400 hover:to-amber-500 text-slate-950 font-bold text-xs shadow-md shadow-amber-500/20">Save Product</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Firebase Settings / Cloud Config Modal -->
    <div id="firebaseSettingsModal" class="fixed inset-0 bg-slate-950/80 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-slate-900 border border-slate-700 rounded-2xl w-full max-w-md overflow-hidden shadow-2xl">
            <div class="bg-slate-800/90 px-6 py-4 border-b border-slate-700 flex justify-between items-center">
                <h3 class="text-base font-bold text-amber-400 flex items-center gap-2">
                    <i class="fa-solid fa-cloud"></i> <span>Firebase Cloud Setup</span>
                </h3>
                <button onclick="closeFirebaseSettingsModal()" class="text-slate-400 hover:text-white text-lg">
                    <i class="fa-solid fa-xmark"></i>
                </button>
            </div>

            <div class="p-6 space-y-4">
                <p class="text-xs text-slate-400 leading-relaxed">
                    Paste your **Firebase Project Web Config** credentials below to enable live, real-time inventory and pricing synchronization across all shop devices and phones.
                </p>

                <div>
                    <label class="block text-xs font-semibold text-slate-300 mb-1">Firebase API Key</label>
                    <input type="text" id="fbApiKey" placeholder="AIzaSy..." 
                        class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-xs text-slate-100 focus:outline-none focus:ring-1 focus:ring-amber-500">
                </div>

                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-semibold text-slate-300 mb-1">Auth Domain</label>
                        <input type="text" id="fbAuthDomain" placeholder="myproject.firebaseapp.com" 
                            class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-xs text-slate-100 focus:outline-none focus:ring-1 focus:ring-amber-500">
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-slate-300 mb-1">Project ID</label>
                        <input type="text" id="fbProjectId" placeholder="myproject-id" 
                            class="w-full bg-slate-950 border border-slate-700 rounded-xl px-3 py-2 text-xs text-slate-100 focus:outline-none focus:ring-1 focus:ring-amber-500">
                    </div>
                </div>

                <div class="pt-2 flex flex-col space-y-2">
                    <button onclick="saveFirebaseConfig()" 
                        class="w-full py-2.5 rounded-xl bg-gradient-to-r from-amber-500 to-amber-600 text-slate-950 font-bold text-xs shadow-md shadow-amber-500/20">
                        Connect & Enable Cloud Sync
                    </button>
                    <button onclick="resetFirebaseConfig()" 
                        class="w-full py-2 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-400 text-xs font-medium">
                        Use Local Storage Mode Only
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- Confirm Delete Modal -->
    <div id="confirmModal" class="fixed inset-0 bg-slate-950/80 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-slate-900 border border-slate-700 rounded-2xl max-w-sm w-full p-6 text-center space-y-4 shadow-2xl">
            <div class="w-12 h-12 rounded-full bg-red-500/10 text-red-500 flex items-center justify-center mx-auto text-xl">
                <i class="fa-solid fa-trash-can"></i>
            </div>
            <h3 class="text-base font-bold text-slate-100">Delete Product?</h3>
            <p class="text-xs text-slate-400">Are you sure you want to delete this product from the inventory?</p>
            <div class="flex justify-center space-x-3 pt-2">
                <button onclick="closeConfirmModal()" class="px-4 py-2 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-300 text-xs font-semibold">Cancel</button>
                <button id="confirmDeleteBtn" class="px-4 py-2 rounded-xl bg-red-600 hover:bg-red-500 text-white text-xs font-semibold shadow-md shadow-red-600/30">Delete</button>
            </div>
        </div>
    </div>

    <!-- Firebase SDK Imports (v11 Modular standard via script) -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, collection, onSnapshot, doc, setDoc, deleteDoc } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // Expose Firebase modules globally for fallback/dynamic configuration
        window.FirebaseModule = {
            initializeApp,
            getAuth,
            signInAnonymously,
            signInWithCustomToken,
            getFirestore,
            collection,
            onSnapshot,
            doc,
            setDoc,
            deleteDoc
        };

        // Auto-Initialize if env variables exist
        if (typeof __firebase_config !== 'undefined' && __firebase_config) {
            try {
                window.initFirebaseSystem(JSON.parse(__firebase_config));
            } catch(e) {
                console.warn('Firebase config error:', e);
            }
        }
    </script>

    <!-- Core Store Logic Script -->
    <script>
        // Store Key for LocalStorage Fallback
        const STORAGE_KEY = 'cmos_computers_inventory_v2';
        const FB_CONFIG_KEY = 'cmos_firebase_config';

        // Initial Sample Products for C MOS Computers
        const initialProducts = [
            {
                id: '1',
                title: 'Dahua 2MP Full-Color HDCVI Dome Camera',
                category: 'CCTV Security',
                cctvBrand: 'Dahua',
                retailPrice: 8500.00,
                wholesalePrice: 6800.00,
                warranty: '2 Years',
                stock: 'In Stock',
                model: 'DH-HAC-HDW1239TLP-A-LED',
                image: 'https://images.unsplash.com/photo-1557597774-9d273605dfa9?w=500&q=80',
                desc: '24/7 Full Color imaging, 3.6mm Fixed Lens, Built-in Microphone, IP67 Weatherproof rating.'
            },
            {
                id: '2',
                title: 'Hikvision 4MP AcuSense Fixed Bullet IP Camera',
                category: 'CCTV Security',
                cctvBrand: 'Hikvision',
                retailPrice: 22500.00,
                wholesalePrice: 18200.00,
                warranty: '2 Years',
                stock: 'In Stock',
                model: 'DS-2CD2043G2-I',
                image: 'https://images.unsplash.com/photo-1589939705384-5185137a7f0f?w=500&q=80',
                desc: 'Human & Vehicle target classification based on deep learning algorithm, H.265+ smart codec.'
            },
            {
                id: '3',
                title: 'Ezviz C6N 1080p Smart Wi-Fi Pan & Tilt Camera',
                category: 'CCTV Security',
                cctvBrand: 'Ezviz',
                retailPrice: 11500.00,
                wholesalePrice: 8900.00,
                warranty: '1 Year',
                stock: 'In Stock',
                model: 'CS-C6N-A0-1C2WFR',
                image: 'https://images.unsplash.com/photo-1558002038-1055907df827?w=500&q=80',
                desc: '360-Degree Panoramic View, Motion Tracking, Auto Smart Night Vision, 2-Way Talk Audio.'
            },
            {
                id: '4',
                title: 'Tiandy 5MP Starlight IR Metal Turret IP Cam',
                category: 'CCTV Security',
                cctvBrand: 'Tiandy',
                retailPrice: 14800.00,
                wholesalePrice: 11400.00,
                warranty: '3 Years',
                stock: 'In Stock',
                model: 'TC-C35WS',
                image: 'https://images.unsplash.com/photo-1557597774-9d273605dfa9?w=500&q=80',
                desc: 'Starlight low-light performance, PoE integrated power, Heavy duty metal housing.'
            },
            {
                id: '5',
                title: 'Imou Cruiser 2 5MP Outdoor Wi-Fi PTZ Camera',
                category: 'CCTV Security',
                cctvBrand: 'Imou',
                retailPrice: 19500.00,
                wholesalePrice: 15600.00,
                warranty: '1 Year',
                stock: 'In Stock',
                model: 'IPC-GS7EP-5M0WE',
                image: 'https://images.unsplash.com/photo-1558002038-1055907df827?w=500&q=80',
                desc: '5MP 3K Resolution, AI Human & Vehicle Detection, Active Siren & Spotlight Deterrent.'
            },
            {
                id: '6',
                title: 'Chinese CCTV 1080p Solar Dual-Lens 4G SIM Cam',
                category: 'CCTV Security',
                cctvBrand: 'Chinese CCTV',
                retailPrice: 13500.00,
                wholesalePrice: 9800.00,
                warranty: '6 Months',
                stock: 'Limited Stock',
                model: 'OEM-SOLAR-4G-V2',
                image: 'https://images.unsplash.com/photo-1589939705384-5185137a7f0f?w=500&q=80',
                desc: 'Dual screen solar powered outdoor 4G SIM camera, pir sensor motion alarm.'
            },
            {
                id: '7',
                title: 'Lexar 512GB NVMe M.2 PCIe Gen3 SSD',
                category: 'Storage & SSDs',
                cctvBrand: 'None',
                retailPrice: 12800.00,
                wholesalePrice: 10400.00,
                warranty: '3 Years',
                stock: 'In Stock',
                model: 'LNM620X512G-RNNNG',
                image: 'https://images.unsplash.com/photo-1597872200969-2b65d56bd16b?w=500&q=80',
                desc: 'High speed read up to 3300MB/s, fast boot drive for laptops, PCs and DVR system.'
            },
            {
                id: '8',
                title: 'TP-Link 300Mbps Wireless N 4G LTE Router',
                category: 'Networking & 4G',
                cctvBrand: 'None',
                retailPrice: 14500.00,
                wholesalePrice: 11900.00,
                warranty: '1 Year',
                stock: 'In Stock',
                model: 'TL-MR6400',
                image: 'https://images.unsplash.com/photo-1544197150-b99a580bb7a8?w=500&q=80',
                desc: 'Plug and play 4G SIM router, ideal for remote CCTV monitoring setups.'
            }
        ];

        // Global Application State
        let products = [];
        let currentFilter = { type: 'all', value: 'all' };
        let searchQuery = '';
        let currentSort = 'default';
        let isAdminView = true; // Admin/Wholesale View by Default
        let firebaseApp = null;
        let firestoreDb = null;
        let firebaseUnsubscribe = null;
        let pendingDeleteId = null;

        const cctvBrands = ['Dahua', 'Hikvision', 'Ezviz', 'Tiandy', 'Imou', 'Chinese CCTV'];
        const generalCategories = [
            'Laptops & Desktops', 
            'Monitors', 
            'Storage & SSDs', 
            'Networking & 4G', 
            'Power & UPS', 
            'Peripherals', 
            'CCTV Accessories', 
            'Services & Repair'
        ];

        // On Page Load Initialization
        window.onload = function() {
            // Check for saved custom Firebase config
            const savedFb = localStorage.getItem(FB_CONFIG_KEY);
            if (savedFb) {
                try {
                    window.initFirebaseSystem(JSON.parse(savedFb));
                } catch(e) {
                    initLocalStorage();
                }
            } else {
                initLocalStorage();
            }

            renderSidebar();
            renderProducts();
        };

        // Initialize Local Storage Fallback
        function initLocalStorage() {
            const stored = localStorage.getItem(STORAGE_KEY);
            if (stored) {
                try {
                    products = JSON.parse(stored);
                } catch(e) {
                    products = initialProducts;
                }
            } else {
                products = initialProducts;
                saveToLocalStorage();
            }
            updateSyncBadge('Local Mode', false);
            renderProducts();
        }

        function saveToLocalStorage() {
            localStorage.setItem(STORAGE_KEY, JSON.stringify(products));
        }

        // Initialize Firebase Cloud Database System
        window.initFirebaseSystem = async function(config) {
            if (!window.FirebaseModule) return;
            try {
                const { initializeApp, getFirestore, collection, onSnapshot, getAuth, signInAnonymously, signInWithCustomToken } = window.FirebaseModule;
                
                firebaseApp = initializeApp(config);
                firestoreDb = getFirestore(firebaseApp);
                const auth = getAuth(firebaseApp);

                // Authenticate
                if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                    await signInWithCustomToken(auth, __initial_auth_token);
                } else {
                    await signInAnonymously(auth);
                }

                const appId = typeof __app_id !== 'undefined' ? __app_id : 'cmos-computers-app';
                const colRef = collection(firestoreDb, 'artifacts', appId, 'public', 'data', 'products');

                // Realtime Snapshot Listener
                if (firebaseUnsubscribe) firebaseUnsubscribe();
                firebaseUnsubscribe = onSnapshot(colRef, (snapshot) => {
                    const fetched = [];
                    snapshot.forEach(doc => {
                        fetched.push({ id: doc.id, ...doc.data() });
                    });

                    if (fetched.length > 0) {
                        products = fetched;
                    } else {
                        // Seed initial products if DB is empty
                        initialProducts.forEach(async (p) => {
                            const { doc, setDoc } = window.FirebaseModule;
                            await setDoc(doc(firestoreDb, 'artifacts', appId, 'public', 'data', 'products', p.id), p);
                        });
                        products = initialProducts;
                    }

                    updateSyncBadge('Cloud Synced', true);
                    renderSidebar();
                    renderProducts();
                }, (error) => {
                    console.error('Firestore sync error:', error);
                    initLocalStorage();
                });

            } catch (err) {
                console.error('Firebase setup failed:', err);
                initLocalStorage();
            }
        };

        // Update Cloud/Sync Indicator Badge
        function updateSyncBadge(label, isCloud) {
            const badge = document.getElementById('dbStatusBadge');
            const text = document.getElementById('syncModeText');
            text.innerText = label;

            if (isCloud) {
                badge.className = "px-2.5 py-1.5 rounded-xl bg-emerald-950 text-emerald-400 border border-emerald-500/30 text-xs font-semibold flex items-center space-x-1.5 transition";
                badge.innerHTML = `<i class="fa-solid fa-cloud-check text-xs"></i><span id="syncModeText">${label}</span>`;
            } else {
                badge.className = "px-2.5 py-1.5 rounded-xl bg-slate-800 text-amber-400 border border-amber-500/30 text-xs font-semibold flex items-center space-x-1.5 transition";
                badge.innerHTML = `<i class="fa-solid fa-cloud-slash text-xs"></i><span id="syncModeText">${label}</span>`;
            }
        }

        // View Mode Toggle (Customer vs Admin Wholesale)
        function toggleViewMode() {
            isAdminView = !isAdminView;
            const btn = document.getElementById('viewModeBtn');
            const label = document.getElementById('viewModeLabel');
            const icon = document.getElementById('viewModeIcon');

            if (isAdminView) {
                btn.className = "px-3 py-2 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs font-semibold border border-slate-700 flex items-center space-x-2 transition";
                label.innerText = 'Admin View';
                icon.className = 'fa-solid fa-shield-halved text-amber-400';
            } else {
                btn.className = "px-3 py-2 rounded-xl bg-cyan-950/60 hover:bg-cyan-900/60 text-cyan-300 text-xs font-semibold border border-cyan-500/40 flex items-center space-x-2 transition";
                label.innerText = 'Customer View';
                icon.className = 'fa-solid fa-eye text-cyan-400';
            }
            renderProducts();
        }

        // Render Sidebar Navigation
        function renderSidebar() {
            // CCTV Brands
            const cctvContainer = document.getElementById('cctvBrandFilters');
            cctvContainer.innerHTML = cctvBrands.map(brand => {
                const count = products.filter(p => p.cctvBrand === brand).length;
                return `
                <button onclick="setFilter('brand', '${brand}')" 
                    id="filter-brand-${brand.replace(/\s+/g, '')}"
                    class="w-full flex items-center justify-between px-3 py-2 rounded-xl text-xs font-medium text-slate-300 hover:bg-slate-800 transition">
                    <span class="flex items-center space-x-2">
                        <span class="w-1.5 h-1.5 rounded-full bg-amber-400"></span>
                        <span>${brand}</span>
                    </span>
                    <span class="text-[10px] bg-slate-950 px-2 py-0.5 rounded-full text-slate-400 font-mono">${count}</span>
                </button>`;
            }).join('');

            // General Computer Hardware Categories
            const generalContainer = document.getElementById('generalCatFilters');
            generalContainer.innerHTML = `
                <button onclick="setFilter('all', 'all')" id="filter-all-all"
                    class="w-full flex items-center justify-between px-3 py-2 rounded-xl text-xs font-medium text-slate-300 hover:bg-slate-800 transition">
                    <span class="flex items-center space-x-2">
                        <i class="fa-solid fa-border-all text-slate-400 text-xs"></i>
                        <span>All Products</span>
                    </span>
                    <span class="text-[10px] bg-slate-950 px-2 py-0.5 rounded-full text-slate-400 font-mono">${products.length}</span>
                </button>
            ` + generalCategories.map(cat => {
                const count = products.filter(p => p.category === cat).length;
                return `
                <button onclick="setFilter('category', '${cat}')"
                    id="filter-category-${cat.replace(/[^a-zA-Z0-9]/g, '')}"
                    class="w-full flex items-center justify-between px-3 py-2 rounded-xl text-xs font-medium text-slate-300 hover:bg-slate-800 transition">
                    <span class="flex items-center space-x-2">
                        <span class="w-1.5 h-1.5 rounded-full bg-cyan-400"></span>
                        <span>${cat}</span>
                    </span>
                    <span class="text-[10px] bg-slate-950 px-2 py-0.5 rounded-full text-slate-400 font-mono">${count}</span>
                </button>`;
            }).join('');

            updateActiveFilterUI();
        }

        // Set Filter Type & Value
        function setFilter(type, value) {
            currentFilter = { type, value };
            updateActiveFilterUI();
            renderProducts();
        }

        function resetFilters() {
            currentFilter = { type: 'all', value: 'all' };
            searchQuery = '';
            document.getElementById('searchInput').value = '';
            updateActiveFilterUI();
            renderProducts();
        }

        function updateActiveFilterUI() {
            document.querySelectorAll('#cctvBrandFilters button, #generalCatFilters button').forEach(btn => {
                btn.classList.remove('bg-amber-500/10', 'text-amber-300', 'border', 'border-amber-500/30', 'font-bold');
            });

            const activeId = currentFilter.type === 'all' 
                ? 'filter-all-all' 
                : `filter-${currentFilter.type}-${currentFilter.value.replace(/[^a-zA-Z0-9]/g, '')}`;
            
            const activeElem = document.getElementById(activeId);
            if (activeElem) {
                activeElem.classList.add('bg-amber-500/10', 'text-amber-300', 'border', 'border-amber-500/30', 'font-bold');
            }

            const titleElem = document.getElementById('currentCategoryTitle');
            let filterTitle = 'All Products';
            if (currentFilter.type === 'brand') filterTitle = `CCTV Brand: ${currentFilter.value}`;
            if (currentFilter.type === 'category') filterTitle = `Category: ${currentFilter.value}`;

            titleElem.innerHTML = `<span>${filterTitle}</span>`;
        }

        // Live Search Handling
        function handleSearch(val) {
            searchQuery = val.toLowerCase().trim();
            renderProducts();
        }

        function handleSort(val) {
            currentSort = val;
            renderProducts();
        }

        // Render Product Cards Grid
        function renderProducts() {
            const grid = document.getElementById('productGrid');
            const emptyState = document.getElementById('emptyState');

            // Apply Filters
            let filtered = products.filter(item => {
                if (currentFilter.type === 'brand' && item.cctvBrand !== currentFilter.value) return false;
                if (currentFilter.type === 'category' && item.category !== currentFilter.value) return false;

                if (searchQuery) {
                    const matchTitle = item.title.toLowerCase().includes(searchQuery);
                    const matchBrand = (item.cctvBrand || '').toLowerCase().includes(searchQuery);
                    const matchModel = (item.model || '').toLowerCase().includes(searchQuery);
                    const matchCat = item.category.toLowerCase().includes(searchQuery);
                    return matchTitle || matchBrand || matchModel || matchCat;
                }
                return true;
            });

            // Apply Sorting
            if (currentSort === 'price-low') {
                filtered.sort((a, b) => parseFloat(a.retailPrice) - parseFloat(b.retailPrice));
            } else if (currentSort === 'price-high') {
                filtered.sort((a, b) => parseFloat(b.retailPrice) - parseFloat(a.retailPrice));
            } else if (currentSort === 'warranty') {
                filtered.sort((a, b) => (a.warranty || '').localeCompare(b.warranty || ''));
            } else if (currentSort === 'stock') {
                filtered.sort((a, b) => (a.stock === 'In Stock' ? -1 : 1));
            }

            document.getElementById('productCountSub').innerText = `Showing ${filtered.length} of ${products.length} total products in inventory`;

            if (filtered.length === 0) {
                grid.innerHTML = '';
                emptyState.classList.remove('hidden');
                emptyState.classList.add('flex');
                return;
            }

            emptyState.classList.add('hidden');
            emptyState.classList.remove('flex');

            grid.innerHTML = filtered.map(item => {
                const isCCTV = item.category === 'CCTV Security' || (item.cctvBrand && item.cctvBrand !== 'None');
                const defaultImg = isCCTV 
                    ? 'https://images.unsplash.com/photo-1557597774-9d273605dfa9?w=500&q=80'
                    : 'https://images.unsplash.com/photo-1597872200969-2b65d56bd16b?w=500&q=80';
                
                const imgSrc = item.image && item.image.startsWith('http') ? item.image : defaultImg;
                const margin = (parseFloat(item.retailPrice) - parseFloat(item.wholesalePrice)).toFixed(2);
                
                let stockBadgeClass = "bg-emerald-500/10 text-emerald-400 border-emerald-500/30";
                if (item.stock === 'Limited Stock') stockBadgeClass = "bg-amber-500/10 text-amber-400 border-amber-500/30";
                if (item.stock === 'Out of Stock') stockBadgeClass = "bg-red-500/10 text-red-400 border-red-500/30";

                return `
                <div class="bg-slate-900/90 rounded-2xl border border-slate-800 overflow-hidden flex flex-col justify-between hover:border-slate-700 transition-all shadow-xl group">
                    <div>
                        <!-- Card Image Header -->
                        <div class="relative h-44 bg-slate-950 overflow-hidden">
                            <img src="${imgSrc}" alt="${item.title}" 
                                onerror="this.onerror=null;this.src='${defaultImg}'"
                                class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300">
                            
                            <!-- Category / CCTV Brand Badge -->
                            <div class="absolute top-3 left-3 flex flex-wrap gap-1.5">
                                ${item.cctvBrand && item.cctvBrand !== 'None' ? `
                                    <span class="px-2.5 py-1 rounded-lg text-[10px] font-extrabold uppercase tracking-wider bg-gradient-to-r from-amber-500 to-amber-600 text-slate-950 shadow-md">
                                        <i class="fa-solid fa-video me-1"></i>${item.cctvBrand}
                                    </span>
                                ` : `
                                    <span class="px-2.5 py-1 rounded-lg text-[10px] font-extrabold uppercase tracking-wider bg-cyan-600 text-white shadow-md">
                                        ${item.category}
                                    </span>
                                `}
                            </div>

                            <!-- Availability Badge -->
                            <div class="absolute bottom-3 left-3">
                                <span class="px-2 py-0.5 rounded-md text-[9px] font-bold border ${stockBadgeClass} uppercase tracking-wider backdrop-blur-md">
                                    ${item.stock || 'In Stock'}
                                </span>
                            </div>

                            <!-- Warranty Badge -->
                            <div class="absolute bottom-3 right-3">
                                <span class="px-2.5 py-1 rounded-lg text-[10px] font-semibold bg-slate-950/90 backdrop-blur-md text-emerald-400 border border-emerald-500/30">
                                    <i class="fa-solid fa-shield-halved me-1"></i>${item.warranty || 'N/A'}
                                </span>
                            </div>
                        </div>

                        <!-- Card Body -->
                        <div class="p-4 space-y-2">
                            ${item.model ? `
                                <div class="text-[10px] font-mono text-amber-400 tracking-wider uppercase">${item.model}</div>
                            ` : ''}
                            <h3 class="font-bold text-slate-100 text-sm leading-snug line-clamp-2">${item.title}</h3>
                            <p class="text-xs text-slate-400 line-clamp-2 leading-relaxed">${item.desc || 'No key specifications provided.'}</p>
                        </div>
                    </div>

                    <!-- Card Pricing Footer -->
                    <div class="p-4 bg-slate-950/60 border-t border-slate-800">
                        <div class="flex items-baseline justify-between mb-3">
                            <!-- Retail Price (LKR) -->
                            <div>
                                <span class="text-[10px] text-slate-400 block uppercase font-semibold">Retail Price</span>
                                <span class="text-lg font-extrabold text-white">LKR ${formatLKR(item.retailPrice)}</span>
                            </div>

                            <!-- Wholesale Price (Admin Only) -->
                            ${isAdminView ? `
                                <div class="text-right">
                                    <span class="text-[10px] text-emerald-400 block uppercase font-semibold">Wholesale</span>
                                    <span class="text-sm font-bold text-emerald-300">LKR ${formatLKR(item.wholesalePrice)}</span>
                                    <span class="text-[9px] text-slate-400 block font-mono">Margin: +Rs.${formatLKR(margin)}</span>
                                </div>
                            ` : ''}
                        </div>

                        <!-- Action Controls -->
                        <div class="flex items-center space-x-2 pt-2 border-t border-slate-800">
                            <!-- WhatsApp Share Button -->
                            <button onclick="shareWhatsApp('${item.id}')" 
                                class="flex-1 py-1.5 px-2 rounded-xl bg-emerald-600/20 hover:bg-emerald-600/30 text-emerald-300 border border-emerald-500/30 text-xs font-semibold flex items-center justify-center space-x-1.5 transition">
                                <i class="fa-brands fa-whatsapp text-emerald-400"></i>
                                <span>Quote</span>
                            </button>

                            ${isAdminView ? `
                                <button onclick="editProduct('${item.id}')" 
                                    class="py-1.5 px-3 rounded-xl bg-slate-800 hover:bg-slate-700 text-slate-300 text-xs font-medium border border-slate-700 transition">
                                    <i class="fa-solid fa-pen"></i>
                                </button>
                                <button onclick="confirmDelete('${item.id}')" 
                                    class="py-1.5 px-3 rounded-xl bg-red-500/10 hover:bg-red-500/20 text-red-400 text-xs font-medium border border-red-500/20 transition">
                                    <i class="fa-solid fa-trash-can"></i>
                                </button>
                            ` : ''}
                        </div>
                    </div>
                </div>`;
            }).join('');
        }

        // Helper Format LKR
        function formatLKR(val) {
            const num = parseFloat(val) || 0;
            return num.toLocaleString('en-LK', { minimumFractionDigits: 2, maximumFractionDigits: 2 });
        }

        // WhatsApp Quote Share Generator
        function shareWhatsApp(id) {
            const item = products.find(p => p.id === id);
            if (!item) return;

            const text = `*C MOS COMPUTERS & TECHNOLOGIES* 🇱🇰
📍 New Bus Stand, Anuradhapura
📞 070 318 2015 / 025 222 8715

📌 *Product Quotation:*
*Item:* ${item.title}
*Model:* ${item.model || 'N/A'}
*Category/Brand:* ${item.cctvBrand && item.cctvBrand !== 'None' ? item.cctvBrand : item.category}
*Warranty:* ${item.warranty}
*Availability:* ${item.stock}

💰 *Retail Price:* LKR ${formatLKR(item.retailPrice)}

Need further assistance or bulk order discounts? Reply to this message!`;

            const encoded = encodeURIComponent(text);
            window.open(`https://wa.me/?text=${encoded}`, '_blank');
        }

        // Modal Handlers
        function openProductModal(editId = null) {
            const modal = document.getElementById('productModal');
            const form = document.getElementById('productForm');
            const modalTitle = document.getElementById('modalTitle');

            form.reset();
            document.getElementById('prodId').value = '';

            if (editId) {
                const item = products.find(p => p.id === editId);
                if (item) {
                    modalTitle.innerHTML = `<i class="fa-solid fa-pen"></i> <span>Edit Product</span>`;
                    document.getElementById('prodId').value = item.id;
                    document.getElementById('prodTitle').value = item.title;
                    document.getElementById('prodCategory').value = item.category;
                    document.getElementById('prodCctvBrand').value = item.cctvBrand || 'None';
                    document.getElementById('prodRetailPrice').value = item.retailPrice;
                    document.getElementById('prodWholesalePrice').value = item.wholesalePrice;
                    document.getElementById('prodWarranty').value = item.warranty;
                    document.getElementById('prodStock').value = item.stock || 'In Stock';
                    document.getElementById('prodModel').value = item.model || '';
                    document.getElementById('prodImage').value = item.image || '';
                    document.getElementById('prodDesc').value = item.desc || '';
                }
            } else {
                modalTitle.innerHTML = `<i class="fa-solid fa-box"></i> <span>Add New Inventory Item</span>`;
                if (currentFilter.type === 'category') document.getElementById('prodCategory').value = currentFilter.value;
                if (currentFilter.type === 'brand') {
                    document.getElementById('prodCategory').value = 'CCTV Security';
                    document.getElementById('prodCctvBrand').value = currentFilter.value;
                }
            }

            modal.classList.remove('hidden');
        }

        function closeProductModal() {
            document.getElementById('productModal').classList.add('hidden');
        }

        function handleModalCategoryChange(val) {
            const brandSelect = document.getElementById('prodCctvBrand');
            if (val !== 'CCTV Security') {
                brandSelect.value = 'None';
            }
        }

        // Save Product (Create / Update with Cloud/Local Dual Support)
        async function saveProduct(e) {
            e.preventDefault();
            
            const id = document.getElementById('prodId').value || Date.now().toString();
            const productData = {
                id,
                title: document.getElementById('prodTitle').value,
                category: document.getElementById('prodCategory').value,
                cctvBrand: document.getElementById('prodCctvBrand').value,
                retailPrice: parseFloat(document.getElementById('prodRetailPrice').value) || 0,
                wholesalePrice: parseFloat(document.getElementById('prodWholesalePrice').value) || 0,
                warranty: document.getElementById('prodWarranty').value,
                stock: document.getElementById('prodStock').value,
                model: document.getElementById('prodModel').value,
                image: document.getElementById('prodImage').value,
                desc: document.getElementById('prodDesc').value
            };

            if (firestoreDb && window.FirebaseModule) {
                // Save to Firebase Firestore Cloud
                try {
                    const { doc, setDoc } = window.FirebaseModule;
                    const appId = typeof __app_id !== 'undefined' ? __app_id : 'cmos-computers-app';
                    await setDoc(doc(firestoreDb, 'artifacts', appId, 'public', 'data', 'products', id), productData);
                } catch(err) {
                    console.error('Error saving to cloud:', err);
                }
            } else {
                // Local Storage Update
                const index = products.findIndex(p => p.id === id);
                if (index !== -1) products[index] = productData;
                else products.unshift(productData);

                saveToLocalStorage();
                renderSidebar();
                renderProducts();
            }

            closeProductModal();
        }

        function editProduct(id) {
            openProductModal(id);
        }

        function confirmDelete(id) {
            pendingDeleteId = id;
            document.getElementById('confirmModal').classList.remove('hidden');
            document.getElementById('confirmDeleteBtn').onclick = function() {
                deleteProduct(pendingDeleteId);
            };
        }

        function closeConfirmModal() {
            pendingDeleteId = null;
            document.getElementById('confirmModal').classList.add('hidden');
        }

        async function deleteProduct(id) {
            if (firestoreDb && window.FirebaseModule) {
                try {
                    const { doc, deleteDoc } = window.FirebaseModule;
                    const appId = typeof __app_id !== 'undefined' ? __app_id : 'cmos-computers-app';
                    await deleteDoc(doc(firestoreDb, 'artifacts', appId, 'public', 'data', 'products', id));
                } catch(err) {
                    console.error('Error deleting from cloud:', err);
                }
            } else {
                products = products.filter(p => p.id !== id);
                saveToLocalStorage();
                renderSidebar();
                renderProducts();
            }
            closeConfirmModal();
        }

        // Firebase Settings Modal Actions
        function openFirebaseSettingsModal() {
            const saved = localStorage.getItem(FB_CONFIG_KEY);
            if (saved) {
                try {
                    const c = JSON.parse(saved);
                    document.getElementById('fbApiKey').value = c.apiKey || '';
                    document.getElementById('fbAuthDomain').value = c.authDomain || '';
                    document.getElementById('fbProjectId').value = c.projectId || '';
                } catch(e){}
            }
            document.getElementById('firebaseSettingsModal').classList.remove('hidden');
        }

        function closeFirebaseSettingsModal() {
            document.getElementById('firebaseSettingsModal').classList.add('hidden');
        }

        function saveFirebaseConfig() {
            const config = {
                apiKey: document.getElementById('fbApiKey').value.trim(),
                authDomain: document.getElementById('fbAuthDomain').value.trim(),
                projectId: document.getElementById('fbProjectId').value.trim(),
            };

            if (config.apiKey && config.projectId) {
                localStorage.setItem(FB_CONFIG_KEY, JSON.stringify(config));
                window.initFirebaseSystem(config);
            }
            closeFirebaseSettingsModal();
        }

        function resetFirebaseConfig() {
            localStorage.removeItem(FB_CONFIG_KEY);
            if (firebaseUnsubscribe) firebaseUnsubscribe();
            firestoreDb = null;
            initLocalStorage();
            closeFirebaseSettingsModal();
        }
    </script>
</body>
</html>
