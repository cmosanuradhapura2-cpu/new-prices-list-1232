<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>C MOS Computers & Technologies - Inventory & Price Catalog</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Firebase SDKs (Compat versions for simple single-file integration) -->
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-database-compat.js"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        brand: { 50: '#eff6ff', 500: '#3b82f6', 600: '#2563eb', 700: '#1d4ed8', dark: '#0f172a' }
                    }
                }
            }
        }
    </script>
</head>
<body class="bg-slate-50 text-slate-800 font-sans antialiased min-h-screen flex flex-col">

    <!-- Top Contact & Store Header -->
    <header class="bg-slate-900 text-white shadow-md">
        <div class="max-w-7xl mx-auto px-4 py-3 flex flex-col md:flex-row justify-between items-center gap-2 text-sm">
            <div class="flex items-center gap-2">
                <i class="fa-solid fa-store text-blue-400"></i>
                <span class="font-semibold">C MOS Computers & Technologies</span>
                <span class="text-slate-400">| New Bus Stand, Anuradhapura</span>
            </div>
            <div class="flex flex-wrap items-center gap-4 text-xs md:text-sm text-slate-300">
                <span><i class="fa-solid fa-phone text-green-400 mr-1"></i> 070 318 2015 / 025 222 8715 / 071 318 2015</span>
                <div class="flex items-center gap-2 bg-slate-800 px-3 py-1 rounded-full border border-slate-700">
                    <span id="syncStatus" class="inline-block w-2.5 h-2.5 rounded-full bg-emerald-400 animate-pulse"></span>
                    <span id="syncText" class="font-medium text-slate-200">Connecting to Cloud...</span>
                </div>
            </div>
        </div>
    </header>

    <!-- Main Navigation Bar -->
    <nav class="bg-white border-b border-slate-200 sticky top-0 z-30 shadow-sm">
        <div class="max-w-7xl mx-auto px-4 py-3 flex flex-wrap justify-between items-center gap-4">
            <div>
                <h1 class="text-xl font-black text-slate-900 tracking-tight flex items-center gap-2">
                    <i class="fa-solid fa-microchip text-blue-600"></i> CMOS <span class="text-blue-600 font-light">POS & Catalog</span>
                </h1>
            </div>
            <div class="flex items-center gap-3">
                <!-- Customer / Admin Mode Toggle Button -->
                <button id="modeToggleBtn" onclick="toggleAdminMode()" class="px-4 py-2 rounded-lg font-semibold text-xs transition flex items-center gap-2 bg-slate-100 text-slate-700 hover:bg-slate-200 border border-slate-300">
                    <i id="modeIcon" class="fa-solid fa-user-shield text-blue-600"></i>
                    <span id="modeText">Customer View (Retail Only)</span>
                </button>
                <!-- Add Product Button (Admin Only) -->
                <button id="addProductBtn" onclick="openModal()" class="px-4 py-2 rounded-lg font-semibold text-xs bg-blue-600 text-white hover:bg-blue-700 transition shadow-sm flex items-center gap-2 hidden">
                    <i class="fa-solid fa-plus"></i> Add Product
                </button>
            </div>
        </div>
    </nav>

    <!-- Search and Category Filters Section -->
    <section class="bg-white border-b border-slate-200 py-4">
        <div class="max-w-7xl mx-auto px-4 space-y-3">
            <!-- Search Bar -->
            <div class="relative">
                <i class="fa-solid fa-search absolute left-4 top-3.5 text-slate-400"></i>
                <input type="text" id="searchInput" oninput="filterProducts()" placeholder="Search by item name, model, brand or category..." class="w-full pl-11 pr-4 py-2.5 bg-slate-50 border border-slate-300 rounded-xl focus:outline-none focus:ring-2 focus:ring-blue-500 text-sm">
            </div>

            <!-- Category Filter Chips -->
            <div class="flex items-center gap-2 overflow-x-auto pb-2 scrollbar-none" id="categoryChips">
                <button onclick="filterCategory('All')" class="cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-blue-600 text-white shadow-sm transition">All Items</button>
                <button onclick="filterCategory('Dahua')" class="cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-700 hover:bg-slate-200 transition">Dahua</button>
                <button onclick="filterCategory('Hikvision')" class="cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-700 hover:bg-slate-200 transition">Hikvision</button>
                <button onclick="filterCategory('Ezviz')" class="cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-700 hover:bg-slate-200 transition">Ezviz</button>
                <button onclick="filterCategory('Tiandy')" class="cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-700 hover:bg-slate-200 transition">Tiandy</button>
                <button onclick="filterCategory('Imou')" class="cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-700 hover:bg-slate-200 transition">Imou</button>
                <button onclick="filterCategory('Chinese Cam')" class="cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-700 hover:bg-slate-200 transition">Chinese Cam</button>
                <button onclick="filterCategory('Laptops & PCs')" class="cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-700 hover:bg-slate-200 transition">Laptops & PCs</button>
                <button onclick="filterCategory('Monitors')" class="cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-700 hover:bg-slate-200 transition">Monitors</button>
                <button onclick="filterCategory('Storage & SSD')" class="cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-700 hover:bg-slate-200 transition">Storage & SSD</button>
                <button onclick="filterCategory('Networking')" class="cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-700 hover:bg-slate-200 transition">Networking / 4G</button>
                <button onclick="filterCategory('Power & UPS')" class="cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-700 hover:bg-slate-200 transition">Power & UPS</button>
                <button onclick="filterCategory('Accessories')" class="cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-700 hover:bg-slate-200 transition">Accessories</button>
            </div>
        </div>
    </section>

    <!-- Main Content Grid -->
    <main class="max-w-7xl mx-auto px-4 py-6 flex-grow w-full">
        <div id="productGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
            <!-- Products injected dynamically -->
        </div>
        <div id="noProducts" class="hidden text-center py-16 text-slate-400">
            <i class="fa-solid fa-box-open text-4xl mb-2"></i>
            <p class="font-medium">No products found matching your search.</p>
        </div>
    </main>

    <!-- Add/Edit Product Modal -->
    <div id="productModal" class="fixed inset-0 bg-black/50 z-50 hidden flex items-center justify-center p-4">
        <div class="bg-white rounded-2xl max-w-lg w-full p-6 shadow-2xl relative">
            <h2 id="modalTitle" class="text-lg font-bold text-slate-900 mb-4">Add New Product</h2>
            <form id="productForm" onsubmit="saveProduct(event)" class="space-y-4">
                <input type="hidden" id="productId">
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">Product Name & Specs</label>
                    <input type="text" id="formName" required placeholder="e.g. Dahua 2MP Full-Color Bullet Camera" class="w-full px-3 py-2 border border-slate-300 rounded-lg text-sm focus:ring-2 focus:ring-blue-500">
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-semibold text-slate-600 mb-1">Category / Brand</label>
                        <select id="formCategory" class="w-full px-3 py-2 border border-slate-300 rounded-lg text-sm bg-white">
                            <option value="Dahua">Dahua</option>
                            <option value="Hikvision">Hikvision</option>
                            <option value="Ezviz">Ezviz</option>
                            <option value="Tiandy">Tiandy</option>
                            <option value="Imou">Imou</option>
                            <option value="Chinese Cam">Chinese Cam</option>
                            <option value="Laptops & PCs">Laptops & PCs</option>
                            <option value="Monitors">Monitors</option>
                            <option value="Storage & SSD">Storage & SSD</option>
                            <option value="Networking">Networking</option>
                            <option value="Power & UPS">Power & UPS</option>
                            <option value="Accessories">Accessories</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-slate-600 mb-1">Warranty Period</label>
                        <input type="text" id="formWarranty" required placeholder="e.g. 2 Years" class="w-full px-3 py-2 border border-slate-300 rounded-lg text-sm">
                    </div>
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-semibold text-slate-600 mb-1">Retail Price (LKR)</label>
                        <input type="number" id="formRetail" required placeholder="5800" class="w-full px-3 py-2 border border-slate-300 rounded-lg text-sm">
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-slate-600 mb-1">Wholesale Price (LKR)</label>
                        <input type="number" id="formWholesale" required placeholder="4900" class="w-full px-3 py-2 border border-slate-300 rounded-lg text-sm">
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">Stock Status</label>
                    <select id="formStock" class="w-full px-3 py-2 border border-slate-300 rounded-lg text-sm bg-white">
                        <option value="In Stock">In Stock</option>
                        <option value="Low Stock">Low Stock</option>
                        <option value="Out of Stock">Out of Stock</option>
                    </select>
                </div>
                <div class="flex justify-end gap-3 pt-3">
                    <button type="button" onclick="closeModal()" class="px-4 py-2 rounded-lg text-sm font-semibold bg-slate-100 text-slate-600 hover:bg-slate-200">Cancel</button>
                    <button type="submit" class="px-5 py-2 rounded-lg text-sm font-semibold bg-blue-600 text-white hover:bg-blue-700 shadow-sm">Save Product</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Footer -->
    <footer class="bg-slate-900 text-slate-400 py-6 mt-auto text-xs text-center border-t border-slate-800">
        <p>© 2026 C MOS Computers & Technologies (New Bus Stand, Anuradhapura). All Rights Reserved.</p>
    </footer>

    <!-- App Logic & Firebase Integration -->
    <script>
        // Exact Firebase credentials provided
        const firebaseConfig = {
            apiKey: "AIzaSyAEb_VuIwhq16T9qC3ZV03rURQdQ3F-NV0",
            authDomain: "new-c-mos.firebaseapp.com",
            databaseURL: "https://new-c-mos-default-rtdb.asia-southeast1.firebasedatabase.app",
            projectId: "new-c-mos",
            storageBucket: "new-c-mos.firebasestorage.app",
            messagingSenderId: "949309834832",
            appId: "1:949309834832:web:d024cb37ce6fda7571b355",
            measurementId: "G-SZ3JR6MZ3F"
        };

        let dbRef = null;
        let isCloudActive = false;

        // Initial default inventory
        const defaultProducts = [
            { id: '1', name: 'Dahua 2MP Full-Color Bullet Camera', category: 'Dahua', retailPrice: 5800, wholesalePrice: 4900, warranty: '2 Years', stockStatus: 'In Stock' },
            { id: '2', name: 'Hikvision 2MP Audio Dome Camera', category: 'Hikvision', retailPrice: 5500, wholesalePrice: 4700, warranty: '2 Years', stockStatus: 'In Stock' },
            { id: '3', name: 'Ezviz C6N 1080p Wi-Fi PT Camera', category: 'Ezviz', retailPrice: 9500, wholesalePrice: 8200, warranty: '1 Year', stockStatus: 'In Stock' },
            { id: '4', name: 'Imou Ranger 2 1080p Smart Camera', category: 'Imou', retailPrice: 9200, wholesalePrice: 7900, warranty: '1 Year', stockStatus: 'In Stock' },
            { id: '5', name: 'Tiandy 2MP Starlight IP Camera', category: 'Tiandy', retailPrice: 6200, wholesalePrice: 5300, warranty: '2 Years', stockStatus: 'In Stock' },
            { id: '6', name: 'Standard 1080p Indoor CCTV Camera (Chinese)', category: 'Chinese Cam', retailPrice: 3800, wholesalePrice: 3100, warranty: '6 Months', stockStatus: 'In Stock' },
            { id: '7', name: 'DDR4 8GB 3200MHz Desktop RAM', category: 'Accessories', retailPrice: 7500, wholesalePrice: 6500, warranty: '3 Years', stockStatus: 'In Stock' },
            { id: '8', name: 'Hikvision 240GB SATA SSD', category: 'Storage & SSD', retailPrice: 6800, wholesalePrice: 5900, warranty: '3 Years', stockStatus: 'In Stock' }
        ];

        let products = [];
        let currentCategory = 'All';
        let isAdminMode = false;

        // Initialize Firebase Realtime Database
        function initFirebase() {
            try {
                firebase.initializeApp(firebaseConfig);
                dbRef = firebase.database().ref('products');

                // Real-time Cloud Listener
                dbRef.on('value', (snapshot) => {
                    const data = snapshot.val();
                    if (data) {
                        products = Object.keys(data).map(key => ({ id: key, ...data[key] }));
                    } else {
                        // Seed default products to Realtime DB if empty
                        defaultProducts.forEach(p => {
                            firebase.database().ref('products/' + p.id).set(p);
                        });
                        products = defaultProducts;
                    }
                    localStorage.setItem('cmos_products', JSON.stringify(products));
                    isCloudActive = true;
                    updateSyncBadge(true, "Live Cloud Synced");
                    renderProducts();
                }, (error) => {
                    console.warn("Firebase sync error fallback to local storage:", error);
                    loadLocalStorage();
                });
            } catch (e) {
                console.warn("Firebase initialization failed:", e);
                loadLocalStorage();
            }
        }

        function loadLocalStorage() {
            isCloudActive = false;
            updateSyncBadge(false, "Offline Mode (Local Storage)");
            products = JSON.parse(localStorage.getItem('cmos_products')) || defaultProducts;
            renderProducts();
        }

        function updateSyncBadge(active, message) {
            const badge = document.getElementById('syncStatus');
            const text = document.getElementById('syncText');
            if (active) {
                badge.className = "inline-block w-2.5 h-2.5 rounded-full bg-emerald-400 animate-pulse";
            } else {
                badge.className = "inline-block w-2.5 h-2.5 rounded-full bg-amber-400";
            }
            text.innerText = message;
        }

        function renderProducts() {
            const grid = document.getElementById('productGrid');
            const noProducts = document.getElementById('noProducts');
            const searchVal = document.getElementById('searchInput').value.toLowerCase();

            grid.innerHTML = '';

            const filtered = products.filter(item => {
                const matchesCat = currentCategory === 'All' || item.category === currentCategory;
                const matchesSearch = item.name.toLowerCase().includes(searchVal) || item.category.toLowerCase().includes(searchVal);
                return matchesCat && matchesSearch;
            });

            if (filtered.length === 0) {
                noProducts.classList.remove('hidden');
                return;
            } else {
                noProducts.classList.add('hidden');
            }

            filtered.forEach(item => {
                const stockColor = item.stockStatus === 'In Stock' ? 'bg-emerald-100 text-emerald-800' : item.stockStatus === 'Low Stock' ? 'bg-amber-100 text-amber-800' : 'bg-rose-100 text-rose-800';
                
                let adminHtml = '';
                if (isAdminMode) {
                    const margin = Number(item.retailPrice) - Number(item.wholesalePrice);
                    adminHtml = `
                        <div class="mt-3 pt-3 border-t border-slate-100 bg-slate-50 p-2.5 rounded-lg space-y-1.5">
                            <div class="flex justify-between items-center text-xs">
                                <span class="font-semibold text-slate-600">Wholesale Price:</span>
                                <span class="font-bold text-slate-900">Rs. ${Number(item.wholesalePrice).toLocaleString()} LKR</span>
                            </div>
                            <div class="flex justify-between items-center text-[11px]">
                                <span class="text-slate-500">Margin Profit:</span>
                                <span class="font-bold text-emerald-600">+Rs. ${Number(margin).toLocaleString()} LKR</span>
                            </div>
                            <div class="flex gap-2 pt-1">
                                <button onclick="editProduct('${item.id}')" class="flex-1 text-blue-600 hover:text-blue-800 text-xs py-1 rounded bg-blue-50 font-semibold border border-blue-200 flex items-center justify-center gap-1">
                                    <i class="fa-solid fa-pen"></i> Edit
                                </button>
                                <button onclick="deleteProduct('${item.id}')" class="text-rose-600 hover:text-rose-800 text-xs px-2.5 py-1 rounded bg-rose-50 font-semibold border border-rose-200">
                                    <i class="fa-solid fa-trash"></i>
                                </button>
                            </div>
                        </div>
                    `;
                }

                const card = document.createElement('div');
                card.className = "bg-white border border-slate-200 rounded-2xl p-5 shadow-sm hover:shadow-md transition flex flex-col justify-between";
                card.innerHTML = `
                    <div>
                        <div class="flex justify-between items-start gap-2 mb-2">
                            <span class="px-2.5 py-1 rounded-md text-xs font-bold bg-blue-50 text-blue-700">${item.category}</span>
                            <span class="px-2.5 py-0.5 rounded-full text-xs font-semibold ${stockColor}">${item.stockStatus}</span>
                        </div>
                        <h3 class="font-bold text-slate-900 text-base mb-2 line-clamp-2">${item.name}</h3>
                        <div class="text-xs text-slate-500 mb-3 flex items-center gap-1.5">
                            <i class="fa-solid fa-shield-halved text-blue-600"></i> Warranty: <span class="font-semibold text-slate-700">${item.warranty}</span>
                        </div>
                    </div>
                    <div>
                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-100 mb-3">
                            <div class="text-xs text-slate-500 font-medium">Retail Price</div>
                            <div class="text-lg font-black text-slate-900">Rs. ${Number(item.retailPrice).toLocaleString()} <span class="text-xs font-normal text-slate-500">LKR</span></div>
                        </div>
                        ${adminHtml}
                        <button onclick="shareWhatsApp('${item.name}', '${item.retailPrice}', '${item.warranty}')" class="w-full mt-2 bg-emerald-600 hover:bg-emerald-700 text-white font-semibold py-2 px-3 rounded-xl text-xs transition flex items-center justify-center gap-2 shadow-sm">
                            <i class="fa-brands fa-whatsapp text-sm"></i> Share Quote
                        </button>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        function filterCategory(cat) {
            currentCategory = cat;
            document.querySelectorAll('.cat-chip').forEach(btn => {
                if (btn.innerText.includes(cat) || (cat === 'All' && btn.innerText === 'All Items')) {
                    btn.className = "cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-blue-600 text-white shadow-sm transition";
                } else {
                    btn.className = "cat-chip px-3.5 py-1.5 rounded-full text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-700 hover:bg-slate-200 transition";
                }
            });
            renderProducts();
        }

        function filterProducts() {
            renderProducts();
        }

        function toggleAdminMode() {
            isAdminMode = !isAdminMode;
            const btnText = document.getElementById('modeText');
            const btnIcon = document.getElementById('modeIcon');
            const addBtn = document.getElementById('addProductBtn');

            if (isAdminMode) {
                btnText.innerText = "Admin View (Wholesale Enabled)";
                btnIcon.className = "fa-solid fa-lock-open text-emerald-600";
                addBtn.classList.remove('hidden');
            } else {
                btnText.innerText = "Customer View (Retail Only)";
                btnIcon.className = "fa-solid fa-user-shield text-blue-600";
                addBtn.classList.add('hidden');
            }
            renderProducts();
        }

        function openModal(isEdit = false) {
            document.getElementById('productModal').classList.remove('hidden');
            if (!isEdit) {
                document.getElementById('modalTitle').innerText = "Add New Product";
                document.getElementById('productForm').reset();
                document.getElementById('productId').value = '';
            }
        }

        function closeModal() {
            document.getElementById('productModal').classList.add('hidden');
        }

        async function saveProduct(e) {
            e.preventDefault();
            const id = document.getElementById('productId').value || Date.now().toString();
            const newItem = {
                id: id,
                name: document.getElementById('formName').value,
                category: document.getElementById('formCategory').value,
                warranty: document.getElementById('formWarranty').value,
                retailPrice: Number(document.getElementById('formRetail').value),
                wholesalePrice: Number(document.getElementById('formWholesale').value),
                stockStatus: document.getElementById('formStock').value
            };

            if (isCloudActive && dbRef) {
                try {
                    await firebase.database().ref('products/' + id).set(newItem);
                } catch (err) {
                    console.error("Cloud save error:", err);
                }
            } else {
                const idx = products.findIndex(p => p.id === id);
                if (idx >= 0) {
                    products[idx] = newItem;
                } else {
                    products.push(newItem);
                }
                localStorage.setItem('cmos_products', JSON.stringify(products));
                renderProducts();
            }

            closeModal();
        }

        function editProduct(id) {
            const item = products.find(p => p.id === id);
            if (!item) return;
            document.getElementById('modalTitle').innerText = "Edit Product";
            document.getElementById('productId').value = item.id;
            document.getElementById('formName').value = item.name;
            document.getElementById('formCategory').value = item.category;
            document.getElementById('formWarranty').value = item.warranty;
            document.getElementById('formRetail').value = item.retailPrice;
            document.getElementById('formWholesale').value = item.wholesalePrice;
            document.getElementById('formStock').value = item.stockStatus;
            document.getElementById('productModal').classList.remove('hidden');
        }

        async function deleteProduct(id) {
            if (confirm("Are you sure you want to delete this product?")) {
                if (isCloudActive && dbRef) {
                    try {
                        await firebase.database().ref('products/' + id).remove();
                    } catch (err) {
                        console.error("Cloud delete error:", err);
                    }
                } else {
                    products = products.filter(p => p.id !== id);
                    localStorage.setItem('cmos_products', JSON.stringify(products));
                    renderProducts();
                }
            }
        }

        function shareWhatsApp(name, retail, warranty) {
            const text = `*C MOS Computers & Technologies* (New Bus Stand, Anuradhapura)\n\n📦 *Product:* ${name}\n🛡️ *Warranty:* ${warranty}\n💵 *Price:* Rs. ${Number(retail).toLocaleString()} LKR\n\n📞 Call/WhatsApp: 070 318 2015 / 025 222 8715 / 071 318 2015`;
            const encoded = encodeURIComponent(text);
            window.open(`https://wa.me/?text=${encoded}`, '_blank');
        }

        // Initialize Firebase on window ready
        window.onload = initFirebase;
    </script>
</body>
</html>
