<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Organigrama Institucional | Estructura Organizacional</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800;900&display=swap');
        
        :root {
            --brand-blue: #1C4AF2;
            --brand-pink: #FA1154;
            --level-1: #1e293b; 
            --level-2: #0F172A; 
            --level-staff: #475569; 
            --level-3: #1E40AF; 
            --level-4: #7C3AED; 
            --level-5: #DB2777; 
            --level-6: #EA580C; 
            --line-color: #cbd5e1;
        }

        body { 
            background-color: #f1f5f9; 
            font-family: 'Inter', sans-serif; 
            margin: 0; 
            color: #334155;
            overflow: hidden;
        }

        /* --- Pantalla de Entrada Premium --- */
        #splash {
            position: fixed;
            inset: 0;
            background: radial-gradient(circle at center, #ffffff 0%, #f3f4f6 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 9999;
            transition: opacity 0.8s cubic-bezier(0.7, 0, 0.3, 1), transform 0.8s cubic-bezier(0.7, 0, 0.3, 1), visibility 0.8s;
        }

        .logo-wrapper {
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            padding: 20px;
        }

        .logo-container-anim {
            position: relative;
            animation: 
                professional-entrance 1.2s cubic-bezier(0.23, 1, 0.32, 1) forwards,
                breathing 4s ease-in-out infinite 1.2s;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .logo-img {
            width: 240px;
            height: auto;
            filter: drop-shadow(0 20px 30px rgba(250, 17, 84, 0.1));
            z-index: 1;
        }

        .shine-effect {
            position: absolute;
            top: 0;
            left: -150%;
            width: 50%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.6), transparent);
            transform: skewX(-20deg);
            z-index: 2;
            animation: shimmer-swipe 3s ease-in-out infinite 1.5s;
        }

        @keyframes professional-entrance {
            0% { opacity: 0; transform: scale(0.8) translateY(30px); filter: blur(8px); }
            100% { opacity: 1; transform: scale(1) translateY(0); filter: blur(0); }
        }

        @keyframes breathing {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.03); }
        }

        @keyframes shimmer-swipe {
            0% { left: -150%; }
            50%, 100% { left: 250%; }
        }

        #splash.hide {
            opacity: 0;
            transform: scale(1.1);
            pointer-events: none;
        }

        /* --- Estructura Organigrama --- */
        .tree-viewport {
            width: 100vw;
            height: calc(100vh - 60px);
            overflow: auto;
            padding: 20px;
            scroll-behavior: smooth;
        }

        .tree-container {
            display: flex;
            justify-content: center;
            min-width: max-content;
            padding: 40px;
            padding-bottom: 120px;
        }

        .tree ul {
            padding-top: 20px;
            position: relative;
            display: flex;
            justify-content: center;
            transition: all 0.3s;
        }

        .tree li {
            text-align: center;
            list-style-type: none;
            position: relative;
            padding: 20px 5px 0 5px;
        }

        .tree li::before, .tree li::after {
            content: '';
            position: absolute; 
            top: 0; 
            right: 50%;
            border-top: 1px solid var(--line-color);
            width: 50%; 
            height: 20px;
        }
        .tree li::after {
            right: auto; 
            left: 50%;
            border-left: 1px solid var(--line-color);
        }

        .tree li:only-child::after, .tree li:only-child::before { display: none; }
        .tree li:only-child { padding-top: 0; }
        .tree li:first-child::after { border-radius: 4px 0 0 0; }
        .tree li:last-child::before { border-right: 1px solid var(--line-color); border-radius: 0 4px 0 0; }
        .tree li:first-child::before, .tree li:last-child::after { border: 0 none; }

        .tree ul ul::before {
            content: '';
            position: absolute; 
            top: 0; 
            left: 50%;
            border-left: 1px solid var(--line-color);
            width: 0; 
            height: 20px;
        }

        .node-wrapper {
            display: inline-flex;
            flex-direction: column;
            align-items: center;
            position: relative;
        }

        .node-card {
            background: white;
            padding: 10px;
            border-radius: 8px;
            border: 1px solid rgba(0, 0, 0, 0.08);
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
            display: inline-block;
            width: 145px;
            position: relative;
            z-index: 10;
            cursor: pointer;
            transition: all 0.2s;
        }

        .node-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.1);
            z-index: 100;
        }

        .staff-card {
            position: absolute;
            left: 165px; 
            top: 50%;
            transform: translateY(-50%);
            width: 120px;
            border-left: 3px solid var(--level-staff);
            background: #f8fafc;
            padding: 8px;
            border-radius: 4px;
            text-align: left;
            box-shadow: 2px 2px 5px rgba(0,0,0,0.05);
            z-index: 5;
        }
        
        .staff-card::after {
            content: '';
            position: absolute;
            left: -20px;
            top: 50%;
            width: 20px; 
            border-top: 1px dashed var(--line-color);
        }

        .level-1 { border-top: 4px solid var(--level-1); }
        .level-2 { border-top: 4px solid var(--level-2); }
        .level-3 { border-top: 4px solid var(--level-3); }
        .level-4 { border-top: 4px solid var(--level-4); }
        .level-5 { border-top: 4px solid var(--level-5); }
        .level-6 { border-top: 4px solid var(--level-6); }

        .collapsed ul { display: none; }

        .toggle-icon {
            position: absolute;
            bottom: -8px;
            left: 50%;
            transform: translateX(-50%);
            width: 16px;
            height: 16px;
            background: white;
            border: 1px solid var(--line-color);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 10px;
            font-weight: 900;
            z-index: 20;
            color: var(--brand-blue);
        }

        .highlight { border: 2px solid var(--brand-pink) !important; background-color: #fff1f2 !important; scale: 1.1; }

        .search-area { 
            position: sticky; top: 0; left: 0; 
            border-bottom: 1px solid #e2e8f0;
            background: white;
            padding: 0 20px; 
            z-index: 1000; 
            display: flex;
            align-items: center;
            justify-content: space-between;
            height: 60px;
        }

        .badge-area {
            font-size: 8px;
            padding: 2px 4px;
            border-radius: 4px;
            font-weight: 700;
            display: inline-block;
            margin-top: 4px;
            text-transform: uppercase;
        }
        .tag-1, .tag-2 { background: #f1f5f9; color: var(--level-1); }
        .tag-3 { background: #eff6ff; color: var(--level-3); }
        .tag-4 { background: #f5f3ff; color: var(--level-4); }
        .tag-5 { background: #fce7f3; color: var(--level-5); }
        .tag-6 { background: #ffedd5; color: var(--level-6); }
    </style>
</head>
<body>

    <div id="splash">
        <div class="logo-wrapper">
            <div class="logo-container-anim">
                <img src="https://i.postimg.cc/wjY3SSP8/ijnij.png" alt="Logo" class="logo-img">
                <div class="shine-effect"></div>
            </div>
        </div>
    </div>

    <div class="search-area">
        <div class="flex items-center gap-4">
            <div class="font-black text-sm uppercase tracking-widest border-l-4 border-blue-600 pl-3">Estructura organizacional</div>
            <div class="relative w-64">
                <input type="text" id="searchInput" placeholder="Buscar colaborador..." 
                    class="w-full pl-8 pr-4 py-1.5 rounded-full border border-gray-200 focus:ring-2 focus:ring-blue-500 outline-none text-xs">
                <span class="absolute left-3 top-2 opacity-30 text-xs">🔍</span>
            </div>
        </div>
        
        <div class="flex gap-2">
            <button onclick="expandAll()" class="px-4 py-1.5 bg-blue-600 text-white text-[10px] font-bold rounded-full uppercase hover:bg-blue-700 transition-colors">Expandir Todo</button>
            <button onclick="collapseAll()" class="px-4 py-1.5 bg-gray-100 text-gray-600 text-[10px] font-bold rounded-full uppercase hover:bg-gray-200 transition-colors">Contraer Todo</button>
        </div>
    </div>

    <div class="tree-viewport" id="viewport">
        <div class="tree-container">
            <div class="tree" id="tree-root"></div>
        </div>
    </div>

    <script>
        const dataSet = [
            // --- CORPORATIVO ---
            ["SOC-01", "Iñaki Pérez García", "CORPORATIVO", "CORPORATIVO", ""],
            ["SOC-02", "Santiago Pérez García", "CORPORATIVO", "CORPORATIVO", ""],

            // --- DG ---
            ["14823", "Rafael Rodríguez Brito", "DIRECTOR GENERAL", "DIRECCION GENERAL", "SOC-SHARED"],
            ["17941", "Nohemí Magos Leal", "CHIEF OF STAFF", "STAFF", "14823"],

            // --- DIRECTORES ---
            ["3101", "Juan Mauricio Vázquez Molina", "DIRECTOR UN AUTOS", "AUTOS", "14823"],
            ["18315", "María Luna López", "DIRECTOR DE CAPITAL HUMANO", "CAPITAL HUMANO", "14823"],
            ["12800", "Daniel López Aldama", "DIRECTOR DATA SCIENCE", "DATA SCIENCE", "14823"],
            ["18378", "Jenzent Adán Jarillo Palacios", "CHIEF FINANCIAL OFFICER", "FINANZAS", "14823"],
            ["15369", "Moisés Rosas Hernández", "DIRECTOR UN GMM", "GMM", "14823"],
            ["13157", "Noé Petriz Escamilla", "CHIEF TECHNOLOGY OFFICER", "TI", "14823"],
            ["18860", "Lili Julieta Chu Pulido", "DIRECCION CLIENTES", "ATC", "14823"],
            ["15401", "Leonel Aguirre Vallejos", "DIRECTOR UN GO", "AHORRA GO", "14823"],
            ["3925", "Romain Calderón Rodríguez", "DIRECTOR JURIDICO", "JURIDICO", "14823"],
            ["14268", "Gabriel Enrique Rosillo Rodríguez", "CHIEF OF GROWTH OFFICER", "MARKETING", "14823"],
            ["10018", "Miguel Ángel Guevara Sandoval", "GERENTE SEG INF, SOP TEC E INFRA", "INFRAESTRUCTURA", "14823"],
            ["1389", "Lucio Hernández Flores", "GERENTE DE MANTENIMIENTO", "SERVICIOS GRALES", "14823"],
            ["1067", "Clara Paulette López Espinosa", "GERENTE UN TRADICIONAL", "AHORRA TRADICIONAL", "14823"],
            ["18790", "Usue Piña Colín", "SUBDIRECTOR DE AUDITORIA", "AUDITORIA", "14823"],

            // --- JURIDICO ---
            ["18420", "OLIVARES CASTILLO MIGUEL ALEJANDRO", "ABOGADO CORPORATIVO", "JURIDICO", "3925"],
            ["17040", "RODRIGUEZ MANCERA MARCO TULIO", "ABOGADO CORPORATIVO", "JURIDICO", "3925"],

            // --- AHORRA GO ---
            ["1050", "Gabriela Aboytes Nieto", "COORDINADOR ADMINISTRATIVO", "AHORRA GO", "15401"],
            ["9620", "Mayra Andrea Gonzalez Alegria", "COORDINADOR DE COMERCIAL Y PROMOTORÍA", "AHORRA GO", "15401"],

            // --- AUTOS (REPORTE DIRECTO JUAN MAURICIO 3101) ---
            ["18806", "Eduwina Galván Martínez", "DIRECTOR COMERCIAL", "AUTOS", "3101"],
            ["8423", "Virginia Gamboa Suasnavart", "DIRECTOR DE CONSERVACIONES", "AUTOS", "3101"],
            ["17238", "ZAVALA DE GANTE EDGAR", "GERENTE DE ATRACCION Y TALENTO AUTOS MX", "AUTOS", "3101"],
            ["16955", "RENTERIA PADILLA JESUS FABRICIO", "GERENTE DE CALIDAD Y PROCESOS", "AUTOS", "3101"],
            ["17462", "LAZARO AQUINO EDUARDO ALEJANDRO", "GERENTE JR E-COMMERCE DIG", "AUTOS", "3101"],
            ["11821", "BALLEZA MORENO ADRIAN", "GERENTE OPERATIVO NEPTUNO", "AUTOS", "3101"],
            ["1143", "CHAVEZ GARCIA YURI DIANA", "GERENTE SR OPERACION VN", "AUTOS", "3101"],
            ["18266", "BARAJAS BARRERA MARIA ALEJANDRA", "GERENTE WORKFORCE MANAGEMENT", "AUTOS", "3101"],
            ["13899", "Yara Lizbeth Guerrero Sánchez", "SUBGERENTE IMPULSO A VENTAS", "AUTOS", "3101"],
            ["6099", "Antonio Vargas Gutiérrez", "SUBGERENTE DE CAPACITACION", "AUTOS", "3101"],
            ["13875", "ALAN YAIR RESENDIZ CALVILLO", "SUBGERENTE CAPACITACION INICIAL", "AUTOS", "3101"],
            ["18741", "CHRISTIAN THOMAS CALDERON SOLIS", "GERENTE DE SINIESTROS", "AUTOS", "3101"],
            
            // --- REDIRECCIONAMIENTOS SOLICITADOS ---
            ["17463", "ARANDA FLORES ALEJANDRO JAVIER", "GERENTE COMERCIAL", "AUTOS", "18806"],
            ["1107", "SANCHEZ TAPIA MARION ARTURO", "GERENTE DE MARCAS", "AUTOS", "1143"],
            ["1123", "SANCHEZ OLVERA BRYAN", "GERENTE DE MARCAS", "AUTOS", "18266"],

            // --- GMM ---
            ["3262", "ALDO IVAN LEON BADILLO", "GERENTE DE CONSERVACIONES", "GMM", "15369"],
            ["9251", "JAVIER NAVA HERNANDEZ", "GERENTE OPERATIVO GMM", "GMM", "15369"],
            ["10537", "LUIS MANUEL GALEANA GONZÁLEZ", "SUBGERENTE DE ATRACCIÓN DE TALENTO Y CAPACITACIÓN", "GMM", "15369"],

            // --- AUTOS (ESTRUCTURA VIRGINIA 8423) ---
            ["15028", "GALLEGOS TELLEZ EDUARDO", "GERENTE DE MISSION CONTROL", "AUTOS", "8423"],
            ["2461", "HERNANDEZ ORTIZ EDWIN JONATHAN", "GERENTE DE CONSERVACIONES", "AUTOS", "8423"],
            ["18097", "JUAREZ MARTINEZ JUANITA", "GERENTE JR DE IMPLEMENTACION", "AUTOS", "8423"],

            // --- OTROS REPORTES ---
            ["18807", "Edgar Jacobo Barbosa Trujillo", "GERENTE COMERCIAL", "AUTOS", "18806"],

            // --- STAFF (NOHEMI 17941) ---
            ["18885", "Ariadna Elizabeth Solorio Rubio", "SUBDIRECTOR PMO", "STAFF", "17941"],
            ["18652", "Ana Elena Robles Pacheco", "GERENTE DE PLANEACION ESTRATEGICA", "STAFF", "17941"],
            ["15539", "María Yolanda Dinora Cortez Montiel", "GERENTE PMO", "STAFF", "17941"],
            ["18861", "Sandra Elizabeth Cuevas Sánchez", "LIDER PMO", "STAFF", "17941"],

            // --- DATA SCIENCE (DANIEL 12800) ---
            ["18791", "Sergio de la Cruz Badillo", "SUBDIRECTOR IA", "DATA SCIENCE", "12800"],
            ["13796", "María Fernanda Olguín Duarte", "GERENTE BI", "DATA SCIENCE", "12800"],
            ["13277", "Josué Hazael Sánchez Huerta", "GERENTE DBA", "DATA SCIENCE", "12800"],

            // --- FINANZAS (JENZENT 18378) ---
            ["14889", "Oscar Armando Aragón Guzmán", "SUBDIRECTOR DE FINANZAS", "FINANZAS", "18378"],
            ["18003", "Guillermo Fabián Valencia Aguilar", "GERENTE CONTABLE", "FINANZAS", "18378"],
            ["15473", "Joshua Jesús Espejel Martínez", "GERENTE DE TESORERIA", "FINANZAS", "18378"],
            ["1009", "Lorena Ballesteros Montero", "GERENTE DE CONTROL DE GASTOS", "FINANZAS", "18378"],

            // --- MARKETING (GABRIEL 14268) ---
            ["13860", "Jessica Arianna Mar Martínez", "SUBDIRECTOR DE MARKETING", "MARKETING", "14268"],
            ["1016", "Leopoldo Vázquez Vargas", "GERENTE FRONT END /UX", "MARKETING", "14268"],
            ["14966", "Stephanie Gabriela López Aguilar", "GERENTE DE UX/IU", "MARKETING", "14268"],
            ["14218", "Sara Alejandra Cadena Serrano", "GERENTE SEM", "MARKETING", "13860"],

            // --- TI (NOE 13157) ---
            ["2843", "Michael Jecsan Pérez Osorio", "GERENTE APP & IA", "TI", "13157"],
            ["14108", "Juan Antonio Vilchis Chaparro", "GERENTE ARQUITECTURA TI", "TI", "13157"],
            ["6182", "César Albert González Mariles", "GERENTE DE QA Y HOMOLOGACION", "TI", "13157"],
            ["12345", "Leopoldo Vázquez Vargas", "GERENTE FRONT END /UX", "TI", "13157"],
            ["1024", "Plácido Josué Sánchez Ayala", "GERENTE JR MIDDLEWARET", "TI", "13157"],

            // --- CAPITAL HUMANO (MARIA LUNA 18315) ---
            ["15166", "José Juan Becerra Badillo", "GERENTE DE ADP", "CAPITAL HUMANO", "18315"],
            ["16845", "Mario Guillermo Pastrana Gómez", "GERENTE AT Y DO", "CAPITAL HUMANO", "18315"],

            // --- ATC (LILI 18860) ---
            ["18808", "Elida Suárez Guevara", "GERENTE DE SOLUCIONES AL CLIENTE", "ATC", "18860"]
        ];

        const areaPriority = { "AUTOS": 1, "GMM": 2, "AHORRA GO": 3, "AHORRA TRADICIONAL": 4, "ATC": 5, "FINANZAS": 6, "MARKETING": 7, "DATA SCIENCE": 8, "TI": 9, "CAPITAL HUMANO": 10, "STAFF": 11 };

        function getLevel(puesto) {
            const p = puesto.toUpperCase();
            if (p === "CORPORATIVO") return 1;
            if (p.includes("DIRECTOR GENERAL")) return 2;
            if (p.includes("CHIEF OF STAFF")) return -1; 
            if (p.includes("DIRECTOR") || p.includes("DIRECCION") || p.includes("CHIEF") || p.includes("OFFICER")) return p.includes("SUBDIRECTOR") ? 4 : 3;
            if (p.includes("SUBDIRECTOR")) return 4;
            if (p.includes("GERENTE") || p.includes("LIDER") || p.includes("COORDINADOR")) return p.includes("SUBGERENTE") ? 6 : 5;
            return 6;
        }

        function buildHierarchy(list) {
            const map = {};
            list.forEach(row => {
                const level = getLevel(row[2]);
                map[row[0]] = { id: row[0], nombre: row[1], puesto: row[2], area: row[3], jefeId: row[4], level: level, children: [] };
            });
            const rootNode = { id: "SOC-SHARED", nombre: "CORPORATIVO", level: 1, children: [] };
            list.forEach(row => {
                const node = map[row[0]];
                if (node.level === 1 || node.id === "17941") return; 
                if (node.jefeId === "SOC-SHARED" || node.jefeId === "SOC-01" || node.jefeId === "SOC-02") {
                    rootNode.children.push(node);
                } else if (node.jefeId && map[node.jefeId]) {
                    map[node.jefeId].children.push(node);
                }
            });
            return { rootNode, map };
        }

        function renderTree(node, map) {
            const hasChildren = node.children.length > 0;
            const li = document.createElement('li');
            const wrapper = document.createElement('div');
            wrapper.className = "node-wrapper";

            if (node.id === "SOC-SHARED") {
                const duo = document.createElement('div');
                duo.className = "flex gap-2 relative";
                ["SOC-01", "SOC-02"].forEach(id => {
                    const s = map[id];
                    if (!s) return;
                    const card = document.createElement('div');
                    card.className = "node-card level-1";
                    card.innerHTML = `<div class="text-[10px] font-black uppercase text-slate-800">${s.nombre}</div>
                                      <div class="text-[7px] font-bold opacity-50">CORPORATIVO</div>`;
                    duo.appendChild(card);
                });
                wrapper.appendChild(duo);
                const toggle = document.createElement('div');
                toggle.className = "toggle-icon";
                toggle.innerText = "-";
                duo.appendChild(toggle);
                duo.onclick = () => {
                    li.classList.toggle('collapsed');
                    toggle.innerText = li.classList.contains('collapsed') ? '+' : '-';
                };
            } else {
                const card = document.createElement('div');
                card.className = `node-card level-${node.level}`;
                card.innerHTML = `
                    <div class="text-[7px] font-bold text-gray-300 text-right mb-1">ID: ${node.id}</div>
                    <div class="text-[10px] font-black uppercase leading-tight text-slate-800 mb-1">${node.nombre}</div>
                    <div class="text-[8px] font-bold uppercase tracking-tight mb-2" style="color: var(--level-${node.level})">${node.puesto}</div>
                    <span class="badge-area tag-${node.level}">${node.area}</span>
                    ${hasChildren ? `<div class="toggle-icon">-</div>` : ''}
                `;
                card.onclick = () => {
                    if (hasChildren) {
                        li.classList.toggle('collapsed');
                        const icon = card.querySelector('.toggle-icon');
                        if(icon) icon.innerText = li.classList.contains('collapsed') ? '+' : '-';
                    }
                };
                wrapper.appendChild(card);
                if (node.id === "14823") {
                    const staffNode = map["17941"];
                    if(staffNode) {
                        const staffCard = document.createElement('div');
                        staffCard.className = "staff-card";
                        staffCard.innerHTML = `
                            <div class="text-[9px] font-black uppercase text-slate-700">${staffNode.nombre}</div>
                            <div class="text-[7px] font-bold uppercase text-slate-400">CHIEF OF STAFF</div>
                        `;
                        wrapper.appendChild(staffCard);
                    }
                }
            }
            li.appendChild(wrapper);
            if (hasChildren) {
                const ul = document.createElement('ul');
                node.children.sort((a,b) => {
                    const pA = areaPriority[a.area] || 99;
                    const pB = areaPriority[b.area] || 99;
                    if (pA !== pB) return pA - pB;
                    return a.level - b.level;
                }).forEach(child => {
                    ul.appendChild(renderTree(child, map));
                });
                li.appendChild(ul);
            }
            return li;
        }

        function expandAll() { document.querySelectorAll('.tree li').forEach(li => { li.classList.remove('collapsed'); const icon = li.querySelector('.toggle-icon'); if(icon) icon.innerText = '-'; }); }
        function collapseAll() { document.querySelectorAll('.tree li').forEach(li => { if(li.querySelector('ul')) { li.classList.add('collapsed'); const icon = li.querySelector('.toggle-icon'); if(icon) icon.innerText = '+'; } }); }

        window.onload = () => {
            const { rootNode, map } = buildHierarchy(dataSet);
            const container = document.getElementById('tree-root');
            const masterUl = document.createElement('ul');
            masterUl.appendChild(renderTree(rootNode, map));
            container.appendChild(masterUl);
            collapseAll();
            setTimeout(() => {
                const splash = document.getElementById('splash');
                splash.classList.add('hide');
                setTimeout(() => splash.style.display = 'none', 800);
            }, 3000);
        };

        document.getElementById('searchInput').addEventListener('input', (e) => {
            const val = e.target.value.toLowerCase().trim();
            document.querySelectorAll('.node-card, .staff-card').forEach(card => {
                card.classList.remove('highlight');
                if (val === "") { card.style.opacity = "1"; return; }
                const match = card.innerText.toLowerCase().includes(val);
                card.style.opacity = match ? "1" : "0.1";
                if (match) {
                    card.classList.add('highlight');
                    let p = card.closest('li')?.parentElement?.closest('li');
                    while(p) { p.classList.remove('collapsed'); const icon = p.querySelector('.toggle-icon'); if(icon) icon.innerText = '-'; p = p.parentElement.closest('li'); }
                }
            });
        });
    </script>
</body>
</html>
