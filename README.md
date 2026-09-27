# Referências Bibliográficas
HTML para referências usando QRcode

     <!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Referências Bibliográficas - Apresentação Acadêmica</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        /* Custom scrollbar for better appearance */
        ::-webkit-scrollbar {
            width: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f5f9;
        }
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 9999px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 min-h-screen flex flex-col justify-between antialiased selection:bg-indigo-500 selection:text-white">

    <!-- Header / Banner Info -->
    <header class="bg-gradient-to-r from-slate-900 via-indigo-950 to-slate-900 text-white pt-10 pb-12 px-4 sm:px-6 shadow-md border-b border-indigo-900/40">
        <div class="max-w-3xl mx-auto text-center">
            <span class="inline-block px-3 py-1 mb-3 text-xs font-semibold uppercase tracking-wider text-indigo-300 bg-indigo-900/60 rounded-full border border-indigo-700/50">
                Referências do Banner
            </span>
            <h1 class="text-2xl sm:text-3xl md:text-4xl font-bold tracking-tight leading-tight mb-4 text-white">
                PROSPECÇÃO GENÔMICA E CARACTERIZAÇÃO DO POTENCIAL ANTIMICROBIANO DAS CEPAS LACTIPLANTIBACILLUS PLANTARUM F01(152) E 9.3B

            </h1>
            <div class="flex flex-wrap justify-center items-center gap-x-4 gap-y-2 text-sm text-slate-300 font-medium mb-4">
                <span class="flex items-center gap-1">
                    <svg class="w-4 h-4 text-indigo-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 4 0 11-8 0 4 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"></path></svg>
                    Gabriel Passos dos Santos, Antônio Fernandes de Carvalho, Cleonice Aparecida de Salgado, Tomás Gomes Reis Veloso, Arthur José Tomaz Soares Pereira.
                </span>
            </div>
            <p class="text-xs sm:text-sm text-slate-400 max-w-xl mx-auto border-t border-slate-800 pt-3">
                Universidade Federal de Viçosa (UFV) • SIA 2026
            </p>
        </div>
    </header>

    <!-- Main Content Container -->
    <main class="max-w-3xl mx-auto px-4 sm:px-6 -mt-6 flex-grow w-full mb-12">
        <!-- Search and Filter Card -->
        <div class="bg-white rounded-2xl shadow-lg border border-slate-200/80 p-4 mb-6 backdrop-blur-sm">
            <div class="flex flex-col sm:flex-row gap-3">
                <div class="relative flex-grow">
                    <div class="absolute inset-y-0 left-0 pl-3.5 flex items-center pointer-events-none text-slate-400">
                        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>
                    </div>
                    <input type="text" id="searchInput" placeholder="Buscar por autor, título ou ano..." 
                        class="w-full pl-10 pr-4 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:bg-white transition-all duration-200 placeholder-slate-400">
                </div>
                <!-- Categories filter -->
                <div class="flex gap-2 overflow-x-auto pb-1 sm:pb-0 scrollbar-none">
                    <button onclick="filterCategory('all')" id="btn-all" class="category-btn active px-4 py-2.5 rounded-xl text-xs font-semibold whitespace-nowrap bg-indigo-600 text-white transition-all shadow-sm">
                        Todas (<span id="count-all">0</span>)
                    </button>
                    <button onclick="filterCategory('Artigo')" id="btn-Artigo" class="category-btn px-4 py-2.5 rounded-xl text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-600 hover:bg-slate-200 transition-all">
                        Artigos
                    </button>
                    <button onclick="filterCategory('Livro')" id="btn-Livro" class="category-btn px-4 py-2.5 rounded-xl text-xs font-semibold whitespace-nowrap bg-slate-100 text-slate-600 hover:bg-slate-200 transition-all">
                        Livros
                    </button>
                </div>
            </div>
        </div>

        <!-- Notification Toast for Copy -->
        <div id="toast" class="fixed bottom-5 right-5 transform translate-y-20 opacity-0 transition-all duration-300 bg-slate-900 text-white text-xs font-medium px-4 py-3 rounded-xl shadow-2xl flex items-center gap-2 z-50 pointer-events-none">
            <svg class="w-4 h-4 text-emerald-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
            <span>Citação copiada para a área de transferência!</span>
        </div>

        <!-- References List Header -->
        <div class="flex items-center justify-between mb-4 px-1">
            <h2 class="text-sm font-bold text-slate-500 uppercase tracking-wider">
                Lista de Obras Consultadas
            </h2>
            <span id="resultsCount" class="text-xs text-slate-400 font-medium">Exibindo 0 referências</span>
        </div>

        <!-- References Cards List -->
        <div id="referencesList" class="space-y-4">
            <!-- Dynamic content loaded via JS -->
        </div>

        <!-- Empty State -->
        <div id="emptyState" class="hidden py-12 text-center bg-white rounded-2xl border border-dashed border-slate-200 p-6">
            <svg class="w-12 h-12 text-slate-300 mx-auto mb-3" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"></path></svg>
            <p class="text-sm font-medium text-slate-600">Nenhuma referência encontrada</p>
            <p class="text-xs text-slate-400 mt-1">Tente buscar por outros termos ou mudar o filtro.</p>
        </div>
    </main>

    <!-- Footer -->
    <footer class="bg-white border-t border-slate-200 py-6 px-4 text-center text-xs text-slate-400">
        <div class="max-w-3xl mx-auto flex flex-col sm:flex-row justify-between items-center gap-3">
            <p>© 2026 • Todos os direitos das obras pertencem aos respectivos autores.</p>
            <p class="flex items-center gap-1">
                <span>Optimizado para acesso via QR Code</span>
                <svg class="w-4 h-4 text-slate-400 inline" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v1m6 11h2m-6 0h-2v4m0-11v3m0 0h.01M12 12h4.01M16 20h4M4 12h4m12 0h.01M5 8h2a1 1 0 001-1V5a1 1 0 00-1-1H5a1 1 0 00-1 1v2a1 1 0 001 1zm12 0h2a1 1 0 001-1V5a1 1 0 00-1-1h-2a1 1 0 00-1 1v2a1 1 0 001 1zM5 20h2a1 1 0 001-1v-2a1 1 0 00-1-1H5a1 1 0 00-1 1v2a1 1 0 001 1z"></path></svg>
            </p>
        </div>
    </footer>

    <script>
        // Array com os dados das referências bibliográficas (Padrão ABNT)
        const referencesData = [
            {
                id: 1,
                authors: "ALKASSAB, Daniah et al.",
                title: "Discovery of leaderless bacteriocins through genome mining.",
                source: "Canadian Journal of Chemistry, v. 102, n. 8, p. 533-543, 2024.",
                type: "Artigo",
                year: "2024",
                doi: "https://doi.org/10.1139/cjc-2023-0209",
                link: "https://doi.org/10.1139/cjc-2023-0209",
                pdfUrl: "https://doi.org/10.1139/cjc-2023-0209",
                keywords: ["genome mining", "bacteriocins", "leaderless"]
            },
            {
                id: 2,
                authors: "LI, Bingyan; HAN, Shiwei; SONG, Dafeng",
                title: "Purification, characterization and membrane-disruptive antibacterial mechanism of a novel bacteriocin SCAY10 from Lactiplantibacillus plantarum SCAY10.",
                source: "Food Chemistry, v. 502, art. 147679, 2026.",
                type: "Artigo",
                year: "2026",
                doi: "https://doi.org/10.1016/j.foodchem.2025.147679",
                link: "https://doi.org/10.1016/j.foodchem.2025.147679",
                pdfUrl: "https://doi.org/10.1016/j.foodchem.2025.147679",
                keywords: ["Lactiplantibacillus plantarum", "bacteriocin", "SCAY10"]
            },
            {
                id: 3,
                authors: "SHEN, Kaisheng; MA, Wenyu; SHI, Linyue; SUN, Haoxuan; DU, Jing; LIU, Guorong",
                title: "The essential role of bacteriocin in Lactiplantibacillus plantarum RX-8 defense against Listeria monocytogenes infection in vitro and in vivo.",
                source: "Food Bioscience, v. 74, art. 107961, 2025.",
                type: "Artigo",
                year: "2025",
                doi: "https://doi.org/10.1016/j.fbio.2025.107961",
                link: "https://doi.org/10.1016/j.fbio.2025.107961",
                pdfUrl: "https://doi.org/10.1016/j.fbio.2025.107961",
                keywords: ["Lactiplantibacillus plantarum", "Listeria monocytogenes", "bacteriocin"]
            }
        ];

        let currentCategory = 'all';

        // Render Function
        function renderReferences(items) {
            const container = document.getElementById('referencesList');
            const emptyState = document.getElementById('emptyState');
            const countText = document.getElementById('resultsCount');

            container.innerHTML = '';
            countText.textContent = `Exibindo ${items.length} referência${items.length !== 1 ? 's' : ''}`;

            if (items.length === 0) {
                emptyState.classList.remove('hidden');
                return;
            } else {
                emptyState.classList.add('hidden');
            }

            items.forEach(ref => {
                const fullCitation = `${ref.authors} ${ref.title} ${ref.source}`;
                
                const card = document.createElement('div');
                card.className = "bg-white rounded-xl shadow-sm border border-slate-200/90 p-5 hover:shadow-md transition-all duration-200 flex flex-col justify-between";
                
                card.innerHTML = `
                    <div>
                        <div class="flex items-center justify-between gap-2 mb-2">
                            <span class="inline-flex items-center px-2.5 py-0.5 rounded-md text-xs font-semibold ${ref.type === 'Artigo' ? 'bg-blue-50 text-blue-700 border border-blue-200/60' : 'bg-emerald-50 text-emerald-700 border border-emerald-200/60'}">
                                ${ref.type}
                            </span>
                            <span class="text-xs font-medium text-slate-400">${ref.year}</span>
                        </div>

                        <!-- ABNT Reference Format -->
                        <p class="text-sm text-slate-700 leading-relaxed font-normal mb-4">
                            <strong class="font-semibold text-slate-900">${escapeHtml(ref.authors)}</strong> 
                            <span class="italic text-slate-800">${escapeHtml(ref.title)}</span> 
                            <span class="text-slate-600">${escapeHtml(ref.source)}</span>
                        </p>
                    </div>

                    <!-- Action Buttons -->
                    <div class="pt-3 border-t border-slate-100 flex flex-wrap items-center justify-between gap-2">
                        <div class="flex flex-wrap items-center gap-2">
                            ${ref.link ? `
                                <a href="${ref.link}" target="_blank" rel="noopener noreferrer" 
                                   class="inline-flex items-center gap-1.5 px-3 py-1.5 bg-indigo-50 hover:bg-indigo-100 text-indigo-700 text-xs font-medium rounded-lg transition-colors">
                                    <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"></path></svg>
                                    Acessar Fonte
                                </a>
                            ` : ''}

                            ${ref.pdfUrl ? `
                                <a href="${ref.pdfUrl}" target="_blank" rel="noopener noreferrer" 
                                   class="inline-flex items-center gap-1.5 px-3 py-1.5 bg-slate-100 hover:bg-slate-200 text-slate-700 text-xs font-medium rounded-lg transition-colors">
                                    <svg class="w-3.5 h-3.5 text-red-500" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 21h10a2 2 0 002-2V9.414a1 1 0 00-.293-.707l-5.414-5.414A1 1 0 0012.586 3H7a2 2 0 00-2 2v14a2 2 0 002 2z"></path></svg>
                                    PDF
                                </a>
                            ` : ''}
                        </div>

                        <!-- Copy Button -->
                        <button onclick="copyCitation('${escapeHtml(fullCitation)}')" 
                                class="inline-flex items-center gap-1 px-2.5 py-1.5 text-xs text-slate-500 hover:text-slate-900 hover:bg-slate-100 rounded-lg transition-colors ml-auto">
                            <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 16H6a2 2 0 01-2-2V6a2 2 0 012-2h8a2 2 0 012 2v2m-6 12h8a2 2 0 002-2v-8a2 2 0 00-2-2h-8a2 2 0 00-2 2v8a2 2 0 002 2z"></path></svg>
                            <span>Copiar Citação</span>
                        </button>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        // Helper function to escape HTML special characters
        function escapeHtml(text) {
            return text
                .replace(/&/g, "&amp;")
                .replace(/</g, "&lt;")
                .replace(/>/g, "&gt;")
                .replace(/"/g, "&quot;")
                .replace(/'/g, "&#039;");
        }

        // Search and Filter Logic
        function filterAndSearch() {
            const query = document.getElementById('searchInput').value.toLowerCase().trim();

            const filtered = referencesData.filter(item => {
                const matchesCategory = (currentCategory === 'all') || (item.type === currentCategory);
                
                const matchesSearch = 
                    item.authors.toLowerCase().includes(query) ||
                    item.title.toLowerCase().includes(query) ||
                    item.source.toLowerCase().includes(query) ||
                    item.year.includes(query) ||
                    item.keywords.some(k => k.toLowerCase().includes(query));

                return matchesCategory && matchesSearch;
            });

            renderReferences(filtered);
        }

        // Category Filter Function
        function filterCategory(category) {
            currentCategory = category;

            // Update Active Buttons UI
            document.querySelectorAll('.category-btn').forEach(btn => {
                btn.classList.remove('bg-indigo-600', 'text-white', 'shadow-sm');
                btn.classList.add('bg-slate-100', 'text-slate-600');
            });

            const activeBtn = document.getElementById(`btn-${category}`);
            if (activeBtn) {
                activeBtn.classList.remove('bg-slate-100', 'text-slate-600');
                activeBtn.classList.add('bg-indigo-600', 'text-white', 'shadow-sm');
            }

            filterAndSearch();
        }

        // Copy Citation to Clipboard using document.execCommand fallback
        function copyCitation(text) {
            const textarea = document.createElement('textarea');
            textarea.value = text;
            textarea.style.position = 'fixed';
            textarea.style.opacity = '0';
            document.body.appendChild(textarea);
            textarea.select();
            
            try {
                document.execCommand('copy');
                showToast();
            } catch (err) {
                console.error('Falha ao copiar:', err);
            } finally {
                document.body.removeChild(textarea);
            }
        }

        // Toast Notification
        function showToast() {
            const toast = document.getElementById('toast');
            toast.classList.remove('translate-y-20', 'opacity-0');
            toast.classList.add('translate-y-0', 'opacity-100');

            setTimeout(() => {
                toast.classList.remove('translate-y-0', 'opacity-100');
                toast.classList.add('translate-y-20', 'opacity-0');
            }, 3000);
        }

        // Event Listeners and Initialization
        document.addEventListener('DOMContentLoaded', () => {
            // Count total items
            document.getElementById('count-all').textContent = referencesData.length;

            // Search Input Event
            document.getElementById('searchInput').addEventListener('input', filterAndSearch);

            // Initial Render
            renderReferences(referencesData);
        });
    </script>
</body>
</html>
