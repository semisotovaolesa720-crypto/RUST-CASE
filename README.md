# RUST-CASE
My firsy project on Git Hub
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rasta Case | Открывай по-гангстерски</title>
    <style>
        /* ---------- Базовые стили ---------- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        @import url('https://semisotovaolesa720-crypto.github.io/RUST-CASE/');

        body {
            background: #0b0806;
            color: #f0e6d0;
            font-family: 'Oswald', sans-serif;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            background-image: radial-gradient(circle at 20% 30%, rgba(200, 50, 50, 0.1) 0%, transparent 30%),
                              radial-gradient(circle at 80% 70%, rgba(50, 200, 50, 0.08) 0%, transparent 40%),
                              repeating-linear-gradient(45deg, rgba(255, 215, 0, 0.02) 0px, rgba(255, 215, 0, 0.02) 2px, transparent 2px, transparent 8px);
        }

        /* ---------- Хедер с цепями и дредами ---------- */
        .header {
            width: 100%;
            max-width: 1400px;
            padding: 20px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(10, 6, 4, 0.9);
            border-bottom: 3px solid #c92a2a;
            border-image: linear-gradient(90deg, #c92a2a, #f5c842, #2e9c2e) 1;
            margin-bottom: 30px;
            flex-wrap: wrap;
            gap: 15px;
            position: relative;
        }
        .header::after {
            content: "";
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 28px;
            text-shadow: 0 0 20px #f5c842;
        }

        .logo {
            font-family: 'Bangers', cursive;
            font-size: 36px;
            letter-spacing: 2px;
            background: linear-gradient(135deg, #c92a2a 30%, #f5c842 60%, #2e9c2e 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: none;
            position: relative;
        }
        .logo span {
            -webkit-text-fill-color: #f5c842;
            font-weight: 400;
        }
        .logo::before {
            content: "🦁";
            margin-right: 8px;
            -webkit-text-fill-color: initial;
            color: #f5c842;
        }

        .user-panel {
            display: flex;
            align-items: center;
            gap: 20px;
        }
        .balance {
            background: #1e1410;
            padding: 8px 20px;
            border-radius: 30px;
            border: 1px solid #f5c842;
            font-weight: 700;
            font-size: 18px;
            color: #f5c842;
            box-shadow: 0 0 20px rgba(245, 200, 66, 0.2);
        }
        .balance i {
            color: #2e9c2e;
            margin-right: 8px;
        }
        .steam-avatar {
            width: 48px;
            height: 48px;
            border-radius: 50%;
            border: 2px solid #c92a2a;
            background: #1e1410;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 26px;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 0 0 15px rgba(201, 42, 42, 0.4);
        }
        .steam-avatar:hover {
            border-color: #f5c842;
            transform: scale(1.1) rotate(-10deg);
        }

        /* ---------- Фильтры с граффити-шрифтом ---------- */
        .filters {
            width: 100%;
            max-width: 1400px;
            padding: 0 30px 20px;
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }
        .filter-btn {
            background: #1e1410;
            border: 1px solid #3d2a1f;
            color: #a08070;
            padding: 10px 24px;
            border-radius: 0;
            font-family: 'Oswald', sans-serif;
            font-size: 16px;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 3px 3px 0 rgba(0,0,0,0.5);
            position: relative;
        }
        .filter-btn::before {
            content: "✊";
            margin-right: 8px;
            opacity: 0.5;
        }
        .filter-btn:hover, .filter-btn.active {
            background: #c92a2a;
            color: #0b0806;
            border-color: #f5c842;
            box-shadow: 5px 5px 0 #f5c842, 0 0 30px rgba(201, 42, 42, 0.3);
            transform: translate(-2px, -2px);
        }
        .filter-btn.active::before {
            opacity: 1;
        }

        /* ---------- Сетка кейсов - карточки с раста-орнаментом ---------- */
        .cases-grid {
            width: 100%;
            max-width: 1400px;
            padding: 0 30px;
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(230px, 1fr));
            gap: 30px;
            margin-bottom: 40px;
        }

        .case-card {
            background: #14100e;
            border-radius: 0;
            overflow: hidden;
            border: 2px solid #2e1f18;
            transition: 0.3s;
            cursor: pointer;
            position: relative;
            display: flex;
            flex-direction: column;
            box-shadow: 6px 6px 0 rgba(0,0,0,0.6);
        }
        .case-card:hover {
            transform: translate(-4px, -4px);
            border-color: #f5c842;
            box-shadow: 10px 10px 0 #c92a2a, 0 0 40px rgba(245, 200, 66, 0.2);
        }
        .case-card::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, #c92a2a, #f5c842, #2e9c2e);
        }

        .case-image {
            width: 100%;
            height: 170px;
            background: #1f1814;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 70px;
            position: relative;
            border-bottom: 2px solid #2e1f18;
        }
        .case-image .rarity-badge {
            position: absolute;
            top: 12px;
            right: 12px;
            background: rgba(0,0,0,0.8);
            padding: 4px 14px;
            font-family: 'Bangers', cursive;
            font-size: 14px;
            letter-spacing: 1px;
            border: 1px solid #f5c842;
            color: #f5c842;
            transform: rotate(5deg);
        }

        .case-info {
            padding: 18px 15px 15px;
            flex: 1;
            display: flex;
            flex-direction: column;
        }
        .case-name {
            font-family: 'Bangers', cursive;
            font-size: 22px;
            color: #f0e6d0;
            margin-bottom: 4px;
            letter-spacing: 0.5px;
        }
        .case-price {
            font-size: 16px;
            color: #a08070;
            margin-bottom: 14px;
            font-weight: 400;
        }
        .case-price strong {
            color: #f5c842;
            font-weight: 700;
        }

        .open-btn {
            background: linear-gradient(135deg, #c92a2a, #a02020);
            border: none;
            padding: 12px 0;
            font-family: 'Bangers', cursive;
            font-size: 20px;
            letter-spacing: 1px;
            color: #f5c842;
            cursor: pointer;
            transition: 0.3s;
            margin-top: auto;
            border: 1px solid #f5c842;
            box-shadow: 3px 3px 0 #1e1410;
            text-shadow: 0 0 10px rgba(245, 200, 66, 0.3);
        }
        .open-btn:hover {
            background: #f5c842;
            color: #0b0806;
            box-shadow: 5px 5px 0 #c92a2a;
            transform: scale(1.02);
        }

        /* ---------- Модальное окно в стиле раста ---------- */
        .modal-overlay {
            display: none;
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.85);
            backdrop-filter: blur(8px);
            z-index: 999;
            justify-content: center;
            align-items: center;
        }
        .modal-overlay.active {
            display: flex;
        }

        .modal-content {
            background: #1a1210;
            border-radius: 0;
            max-width: 550px;
            width: 90%;
            padding: 30px;
            border: 3px solid #f5c842;
            box-shadow: 0 0 60px rgba(201, 42, 42, 0.5), 12px 12px 0 #1e1410;
            text-align: center;
            animation: modalPop 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
        }
        .modal-content::before {
            content: "✊🏿";
            position: absolute;
            top: -20px;
            left: -20px;
            font-size: 40px;
            opacity: 0.3;
            transform: rotate(-15deg);
        }
        .modal-content::after {
            content: "🔥";
            position: absolute;
            bottom: -20px;
            right: -20px;
            font-size: 40px;
            opacity: 0.3;
            transform: rotate(15deg);
        }
        @keyframes modalPop {
            0% { transform: scale(0.5) rotate(-10deg); opacity: 0; }
            100% { transform: scale(1) rotate(0deg); opacity: 1; }
        }

        .modal-title {
            font-family: 'Bangers', cursive;
            font-size: 32px;
            color: #f5c842;
            margin-bottom: 20px;
            text-shadow: 0 0 20px rgba(245, 200, 66, 0.4);
            letter-spacing: 2px;
        }

        .slot-machine {
            background: #0f0b09;
            border: 2px solid #2e1f18;
            padding: 30px 10px;
            margin-bottom: 25px;
            min-height: 160px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 80px;
            transition: 0.3s;
            box-shadow: inset 0 0 40px rgba(0,0,0,0.8);
        }
        .slot-machine.spinning {
            animation: slotSpin 1.4s cubic-bezier(0.25, 0.1, 0.15, 1) forwards;
        }
        @keyframes slotSpin {
            0% { transform: scale(0.6) rotate(-20deg); opacity: 0.2; filter: blur(4px); }
            30% { transform: scale(1.4) rotate(10deg); opacity: 1; filter: blur(0); }
            60% { transform: scale(0.8) rotate(-10deg); }
            100% { transform: scale(1) rotate(0deg); opacity: 1; filter: blur(0); }
        }

        .result-details {
            font-family: 'Oswald', sans-serif;
            font-size: 22px;
            margin-bottom: 25px;
        }
        .result-details .item-name {
            font-weight: 700;
            color: #f5f0e0;
            text-shadow: 0 0 15px rgba(245, 200, 66, 0.2);
        }
        .result-details .item-rarity {
            display: inline-block;
            padding: 4px 20px;
            font-family: 'Bangers', cursive;
            font-size: 18px;
            letter-spacing: 1px;
            margin-top: 8px;
            border: 1px solid;
        }

        .modal-close-btn {
            background: #2e1f18;
            border: 2px solid #f5c842;
            color: #f5c842;
            padding: 12px 40px;
            font-family: 'Bangers', cursive;
            font-size: 20px;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 3px 3px 0 #0b0806;
        }
        .modal-close-btn:hover {
            background: #c92a2a;
            color: #0b0806;
            border-color: #c92a2a;
            box-shadow: 5px 5px 0 #f5c842;
            transform: translate(-2px, -2px);
        }

        /* ---------- Адаптив ---------- */
        @media (max-width: 768px) {
            .header {
                flex-direction: column;
                align-items: stretch;
                padding: 15px;
            }
            .user-panel {
                justify-content: space-between;
            }
            .logo { font-size: 28px; }
            .cases-grid {
                grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
                gap: 20px;
                padding: 0 15px;
            }
            .case-image { height: 130px; font-size: 50px; }
            .modal-content { padding: 20px; }
        }

        @media (max-width: 480px) {
            .cases-grid {
                grid-template-columns: 1fr 1fr;
                gap: 12px;
            }
            .filter-btn { font-size: 13px; padding: 6px 12px; }
        }

        /* ---------- Дополнительные брутальные детали ---------- */
        .footer {
            margin-top: auto;
            padding: 20px;
            color: #5a4a3a;
            font-size: 14px;
            border-top: 1px solid #2e1f18;
            width: 100%;
            text-align: center;
            background: #0b0806;
        }
        .footer span {
            color: #c92a2a;
        }
        .footer .rasta-flag {
            display: inline-block;
            width: 20px;
            height: 20px;
            background: linear-gradient(180deg, #c92a2a 33%, #f5c842 33% 66%, #2e9c2e 66%);
            margin: 0 8px;
            vertical-align: middle;
        }
    </style>
</head>
<body>
    <!-- Шапка с цепями -->
    <header class="header">
        <div class="logo">Rasta<span>Case</span></div>
        <div class="user-panel">
            <div class="balance"><i>💰</i> 1 250</div>
            <div class="steam-avatar">🦁</div>
        </div>
    </header>

    <!-- Фильтры с раста-символикой -->
    <div class="filters">
        <button class="filter-btn active">Все</button>
        <button class="filter-btn">🔥 Базовые</button>
        <button class="filter-btn">⚡ Легенды</button>
        <button class="filter-btn">💀 Мифические</button>
        <button class="filter-btn">🗡️ Ножевые</button>
    </div>

    <!-- Сетка кейсов -->
    <div class="cases-grid" id="casesContainer">
        <!-- Генерируется JS -->
    </div>

    <!-- Модальное окно -->
    <div class="modal-overlay" id="modalOverlay">
        <div class="modal-content">
            <div class="modal-title">🦁 Открывай!</div>
            <div class="slot-machine" id="slotDisplay">❓</div>
            <div class="result-details" id="resultDetails">
                <div class="item-name">Нажми на кейс</div>
                <div class="item-rarity" style="background:#2e1f18; color:#a08070; border-color:#2e1f18;">Жди...</div>
            </div>
            <button class="modal-close-btn" id="modalCloseBtn">✊ Закрыть</button>
        </div>
    </div>

    <footer class="footer">
        <span class="rasta-flag"></span> One Love, One Case <span class="rasta-flag"></span>
    </footer>

    <script>
        // ---------- Данные кейсов (раста-тематика) ----------
        const casesData = [
            { id: 1, name: 'Базовый джа', price: 100, emoji: '🌿', rarity: 'Common' },
            { id: 2, name: 'Редкий мари', price: 250, emoji: '🔥', rarity: 'Rare' },
            { id: 3, name: 'Легендарный ваб', price: 500, emoji: '⚡', rarity: 'Legendary' },
            { id: 4, name: 'Мифический львиный', price: 1200, emoji: '🦁', rarity: 'Mythic' },
            { id: 5, name: 'Ножевой растаман', price: 2500, emoji: '🗡️', rarity: 'Knife' },
            { id: 6, name: 'Кейс ганжи', price: 50, emoji: '🍀', rarity: 'Common' },
            { id: 7, name: 'Кейс Боба', price: 999, emoji: '🎸', rarity: 'Legendary' },
            { id: 8, name: 'Кейс дракона', price: 3500, emoji: '🐉', rarity: 'Mythic' },
        ];

        const rarityColors = {
            'Common': '#6c8c9c',
            'Rare': '#4a7db5',
            'Legendary': '#b57c4a',
            'Mythic': '#c44a7a',
            'Knife': '#f5c842'
        };

        function renderCases() {
            const container = document.getElementById('casesContainer');
            container.innerHTML = '';
            casesData.forEach(c => {
                const card = document.createElement('div');
                card.className = 'case-card';
                card.dataset.id = c.id;
                card.innerHTML = `
                    <div class="case-image" style="background: #1f1814;">
                        <span>${c.emoji}</span>
                        <span class="rarity-badge" style="color:${rarityColors[c.rarity]}; border-color:${rarityColors[c.rarity]};">${c.rarity}</span>
                    </div>
                    <div class="case-info">
                        <div class="case-name">${c.name}</div>
                        <div class="case-price">Цена: <strong>${c.price} монет</strong></div>
                        <button class="open-btn" data-id="${c.id}">Открыть</button>
                    </div>
                `;
                container.appendChild(card);
            });

            document.querySelectorAll('.open-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    e.stopPropagation();
                    const caseId = parseInt(btn.dataset.id);
                    openCase(caseId);
                });
            });
        }

        // ---------- Открытие кейса с раста-эффектами ----------
        function openCase(caseId) {
            const modal = document.getElementById('modalOverlay');
            const slot = document.getElementById('slotDisplay');
            const details = document.getElementById('resultDetails');

            modal.classList.add('active');

            slot.textContent = '🎰';
            slot.className = 'slot-machine spinning';
            details.innerHTML = `<div class="item-name">⏳ Крутим...</div>
                                 <div class="item-rarity" style="background:#2e1f18; color:#a08070; border-color:#2e1f18;">Джа-мон!</div>`;

            setTimeout(() => {
                // Симуляция выпадения с весами (как в прошлом примере)
                const items = [
                    { name: 'Взрывко', rarity: 'Common', emoji: '' },
                    { name: 'Страшный сосед', rarity: 'Rare', emoji: '🔥' },
                    { name: 'Бомж', rarity: 'Legendary', emoji: '⚡' },
                    { name: ' Ниндзя', rarity: 'Mythic', emoji: '🦁' },
                    { name: '  Двушка-тайм', rarity: 'Knife', emoji: '🗡️' },
                ];
                const weights = [50, 25, 10, 5, 0.2];
                const total = weights.reduce((a,b) => a+b, 0);
                let rand = Math.random() * total;
                let selected = items[0];
                let cum = 0;
                for (let i = 0; i < items.length; i++) {
                    cum += weights[i];
                    if (rand < cum) { selected = items[i]; break; }
                }

                slot.textContent = selected.emoji;
                slot.className = 'slot-machine';
                const color = rarityColors[selected.rarity] || '#f5c842';
                details.innerHTML = `
                    <div class="item-name">${selected.name}</div>
                    <div class="item-rarity" style="background:${color}; color:#0b0806; border-color:${color};">${selected.rarity}</div>
                `;
                // Здесь можно добавить запрос на сервер
            }, 1500);
        }

        // Закрытие модалки
        document.getElementById('modalCloseBtn').addEventListener('click', () => {
            document.getElementById('modalOverlay').classList.remove('active');
        });
        document.getElementById('modalOverlay').addEventListener('click', (e) => {
            if (e.target === e.currentTarget) {
                document.getElementById('modalOverlay').classList.remove('active');
            }
        });

        // Фильтры (демонстрация)
        document.querySelectorAll('.filter-btn').forEach(btn => {
            btn.addEventListener('click', function() {
                document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
                this.classList.add('active');
                // Здесь можно реализовать фильтрацию
            });
        });

        renderCases();
    </script>
</body>
</html>
