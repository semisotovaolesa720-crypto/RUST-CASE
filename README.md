# RUST-CASE
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RUST-CASE   - Открой свой кейс</title>
    <style>
        /* ---------- Общие стили ---------- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Roboto, system-ui, sans-serif;
        }

        body {
            background: #0b0e14;
            color: #e0e6f0;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        /* ---------- Шапка ---------- */
        .header {
            width: 100%;
            max-width: 1400px;
            padding: 20px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(18, 24, 34, 0.8);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid #2a3346;
            margin-bottom: 30px;
            flex-wrap: wrap;
            gap: 15px;
        }

        .logo {
            font-size: 28px;
            font-weight: 800;
            background: linear-gradient(45deg, #f5b042, #ff6b6b);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: 1px;
        }
        .logo span {
            font-weight: 300;
            color: #7e8ba3;
            -webkit-text-fill-color: #7e8ba3;
        }

        .user-panel {
            display: flex;
            align-items: center;
            gap: 20px;
        }
        .balance {
            background: #1e2738;
            padding: 8px 18px;
            border-radius: 30px;
            border: 1px solid #3d4a62;
            font-weight: 600;
            font-size: 16px;
        }
        .balance i {
            color: #f5b042;
            margin-right: 8px;
        }
        .steam-avatar {
            width: 44px;
            height: 44px;
            border-radius: 50%;
            border: 2px solid #5c6f92;
            background: #2a3346;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 22px;
            cursor: pointer;
            transition: 0.3s;
        }
        .steam-avatar:hover {
            border-color: #f5b042;
            transform: scale(1.05);
        }

        /* ---------- Фильтры ---------- */
        .filters {
            width: 100%;
            max-width: 1400px;
            padding: 0 30px 20px;
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
        }
        .filter-btn {
            background: #1a2332;
            border: none;
            color: #a0b3cc;
            padding: 8px 20px;
            border-radius: 30px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.3s;
            border: 1px solid transparent;
        }
        .filter-btn:hover, .filter-btn.active {
            background: #2c3a54;
            color: #fff;
            border-color: #f5b042;
            box-shadow: 0 0 15px rgba(245, 176, 66, 0.2);
        }

        /* ---------- Сетка кейсов ---------- */
        .cases-grid {
            width: 100%;
            max-width: 1400px;
            padding: 0 30px;
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }

        .case-card {
            background: #141c2a;
            border-radius: 16px;
            overflow: hidden;
            border: 1px solid #273141;
            transition: 0.3s;
            cursor: pointer;
            position: relative;
            display: flex;
            flex-direction: column;
        }
        .case-card:hover {
            transform: translateY(-8px);
            border-color: #f5b042;
            box-shadow: 0 10px 40px rgba(245, 176, 66, 0.15);
        }

        .case-image {
            width: 100%;
            height: 160px;
            background: #1f2a3d;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 60px;
            position: relative;
        }
        .case-image .rarity-badge {
            position: absolute;
            top: 10px;
            right: 10px;
            background: rgba(0,0,0,0.7);
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 700;
            letter-spacing: 0.5px;
            color: #f5b042;
            border: 1px solid #f5b042;
        }

        .case-info {
            padding: 15px;
            flex: 1;
            display: flex;
            flex-direction: column;
        }
        .case-name {
            font-size: 18px;
            font-weight: 700;
            margin-bottom: 6px;
            color: #f0f4fc;
        }
        .case-price {
            font-size: 15px;
            color: #8da0c0;
            margin-bottom: 12px;
        }
        .case-price strong {
            color: #f5b042;
            font-weight: 700;
        }

        .open-btn {
            background: linear-gradient(135deg, #f5b042, #f28b3a);
            border: none;
            padding: 10px 0;
            border-radius: 30px;
            font-weight: 700;
            font-size: 16px;
            color: #0b0e14;
            cursor: pointer;
            transition: 0.3s;
            margin-top: auto;
        }
        .open-btn:hover {
            transform: scale(1.02);
            box-shadow: 0 0 25px rgba(245, 176, 66, 0.5);
        }

        /* ---------- Модальное окно (открытие кейса) ---------- */
        .modal-overlay {
            display: none;
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.8);
            backdrop-filter: blur(6px);
            z-index: 999;
            justify-content: center;
            align-items: center;
        }
        .modal-overlay.active {
            display: flex;
        }

        .modal-content {
            background: #192231;
            border-radius: 30px;
            max-width: 550px;
            width: 90%;
            padding: 30px;
            border: 1px solid #3d4a62;
            box-shadow: 0 30px 60px rgba(0,0,0,0.7);
            text-align: center;
            animation: modalPop 0.4s ease;
        }
        @keyframes modalPop {
            0% { transform: scale(0.8) translateY(30px); opacity: 0; }
            100% { transform: scale(1) translateY(0); opacity: 1; }
        }

        .modal-title {
            font-size: 24px;
            font-weight: 700;
            margin-bottom: 20px;
            color: #f5b042;
        }

        .slot-machine {
            background: #0f1622;
            border-radius: 20px;
            padding: 30px 10px;
            margin-bottom: 25px;
            border: 1px solid #2c3a54;
            min-height: 150px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 70px;
            transition: 0.3s;
        }
        .slot-machine.spinning {
            animation: slotSpin 1.2s cubic-bezier(0.25, 0.1, 0.15, 1) forwards;
        }
        @keyframes slotSpin {
            0% { transform: scale(0.8) rotate(-10deg); opacity: 0.3; }
            30% { transform: scale(1.3) rotate(5deg); opacity: 1; }
            60% { transform: scale(0.9) rotate(-5deg); }
            100% { transform: scale(1) rotate(0deg); opacity: 1; }
        }

        .result-details {
            font-size: 20px;
            margin-bottom: 20px;
        }
        .result-details .item-name {
            font-weight: 700;
            color: #f5f9ff;
        }
        .result-details .item-rarity {
            display: inline-block;
            padding: 4px 16px;
            border-radius: 30px;
            font-size: 14px;
            font-weight: 700;
            margin-top: 6px;
        }

        .modal-close-btn {
            background: #2c3a54;
            border: none;
            color: #fff;
            padding: 12px 30px;
            border-radius: 40px;
            font-weight: 600;
            font-size: 16px;
            cursor: pointer;
            transition: 0.3s;
        }
        .modal-close-btn:hover {
            background: #3d4d6e;
        }

        /* ---------- Адаптивность ---------- */
        @media (max-width: 768px) {
            .header {
                flex-direction: column;
                align-items: stretch;
                gap: 10px;
                padding: 15px;
            }
            .user-panel {
                justify-content: space-between;
            }
            .cases-grid {
                grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
                gap: 15px;
                padding: 0 15px;
            }
            .case-image {
                height: 120px;
                font-size: 40px;
            }
            .modal-content {
                padding: 20px;
            }
        }

        @media (max-width: 480px) {
            .cases-grid {
                grid-template-columns: 1fr 1fr;
                gap: 10px;
            }
            .filters {
                gap: 8px;
                padding: 0 10px;
            }
            .filter-btn {
                font-size: 12px;
                padding: 6px 14px;
            }
        }
    </style>
</head>
<body>
    <!-- Шапка -->
    <header class="header">
        <div class="logo">🎲 Case<span>Battle</span></div>
        <div class="user-panel">
            <div class="balance"><i>💰</i> 1 250</div>
            <div class="steam-avatar">🦊</div>
        </div>
    </header>

    <!-- Фильтры -->
    <div class="filters">
        <button class="filter-btn active">Все</button>
        <button class="filter-btn">Базовые</button>
        <button class="filter-btn">Легендарные</button>
        <button class="filter-btn">Мифические</button>
        <button class="filter-btn">Ножевые</button>
    </div>

    <!-- Сетка кейсов (данные из массива) -->
    <div class="cases-grid" id="casesContainer">
        <!-- Карточки будут сгенерированы JS -->
    </div>

    <!-- Модальное окно -->
    <div class="modal-overlay" id="modalOverlay">
        <div class="modal-content">
            <div class="modal-title">🎁 Открытие кейса</div>
            <div class="slot-machine" id="slotDisplay">❓</div>
            <div class="result-details" id="resultDetails">
                <div class="item-name">Нажмите на кейс</div>
                <div class="item-rarity" style="background:#2c3a54; color:#a0b3cc;">Ожидание...</div>
            </div>
            <button class="modal-close-btn" id="modalCloseBtn">Закрыть</button>
        </div>
    </div>

    <script>
        // ---------- Данные кейсов (имитация) ----------
        const casesData = [
            { id: 1, name: 'Базовый кейс', price: 100, emoji: '📦', rarity: 'Common' },
            { id: 2, name: 'Редкий кейс', price: 250, emoji: '🔮', rarity: 'Rare' },
            { id: 3, name: 'Легендарный кейс', price: 500, emoji: '⚡', rarity: 'Legendary' },
            { id: 4, name: 'Мифический кейс', price: 1200, emoji: '🔥', rarity: 'Mythic' },
            { id: 5, name: 'Ножевой кейс', price: 2500, emoji: '🗡️', rarity: 'Knife' },
            { id: 6, name: 'Кейс удачи', price: 50, emoji: '🍀', rarity: 'Common' },
            { id: 7, name: 'Кейс бессмертия', price: 999, emoji: '💀', rarity: 'Legendary' },
            { id: 8, name: 'Кейс дракона', price: 3500, emoji: '🐉', rarity: 'Mythic' },
        ];

        // Цвета редкостей
        const rarityColors = {
            'Common': '#6c8c9c',
            'Rare': '#4a7db5',
            'Legendary': '#b57c4a',
            'Mythic': '#c44a7a',
            'Knife': '#f5b042'
        };

        // Функция рендера карточек
        function renderCases() {
            const container = document.getElementById('casesContainer');
            container.innerHTML = '';
            casesData.forEach(c => {
                const card = document.createElement('div');
                card.className = 'case-card';
                card.dataset.id = c.id;
                card.innerHTML = `
                    <div class="case-image" style="background: #1f2a3d;">
                        <span style="font-size:50px;">${c.emoji}</span>
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

            // Вешаем обработчики на кнопки открытия
            document.querySelectorAll('.open-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    e.stopPropagation();
                    const caseId = parseInt(btn.dataset.id);
                    openCase(caseId);
                });
            });
        }

        // ---------- Логика открытия кейса (симуляция) ----------
        function openCase(caseId) {
            const modal = document.getElementById('modalOverlay');
            const slot = document.getElementById('slotDisplay');
            const details = document.getElementById('resultDetails');

            // Показываем модалку
            modal.classList.add('active');

            // Анимация прокрутки
            slot.textContent = '🎰';
            slot.className = 'slot-machine spinning';
            details.innerHTML = `<div class="item-name">⏳ Определяем результат...</div>
                                 <div class="item-rarity" style="background:#2c3a54; color:#a0b3cc;">Подождите...</div>`;

            // Имитация запроса к серверу (задержка 1.5с)
            setTimeout(() => {
                // Случайный выбор предмета (для демонстрации)
                const items = [
                    { name: 'Обычный скин', rarity: 'Common', emoji: '🎨' },
                    { name: 'Редкий скин', rarity: 'Rare', emoji: '🌟' },
                    { name: 'Легендарный скин', rarity: 'Legendary', emoji: '⚜️' },
                    { name: 'Мифический скин', rarity: 'Mythic', emoji: '👑' },
                    { name: 'Нож-бабочка', rarity: 'Knife', emoji: '🔪' },
                ];

                // Симулируем вероятности (как в реальном коде)
                const weights = [50, 25, 10, 5, 0.2]; // шансы в процентах
                const total = weights.reduce((a,b) => a+b, 0);
                let rand = Math.random() * total;
                let selected = items[0];
                let cum = 0;
                for (let i = 0; i < items.length; i++) {
                    cum += weights[i];
                    if (rand < cum) { selected = items[i]; break; }
                }

                // Отображаем результат
                slot.textContent = selected.emoji;
                slot.className = 'slot-machine'; // убираем анимацию
                const color = rarityColors[selected.rarity] || '#fff';
                details.innerHTML = `
                    <div class="item-name">${selected.name}</div>
                    <div class="item-rarity" style="background:${color}; color:#0b0e14;">${selected.rarity}</div>
                `;

                // Здесь можно добавить списание баланса и другие действия
                // (в реальном проекте - AJAX-запрос к серверу)
            }, 1500);
        }

        // Закрытие модалки
        document.getElementById('modalCloseBtn').addEventListener('click', () => {
            document.getElementById('modalOverlay').classList.remove('active');
        });
        // Закрытие по клику на оверлей
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
                // Здесь можно реализовать фильтрацию кейсов по категории
                // (в примере просто сброс)
                renderCases(); // перерисовка (можно убрать, если данные не меняются)
            });
        });

        // Инициализация
        renderCases();
    </script>
</body>
</html>
