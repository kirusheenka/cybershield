<section id="emergency">
    <div class="container">
        <div class="card" style="border-top-color: var(--accent); background: #fef2f2;">
            <h2 style="color: var(--accent);">🆘 Если вас обманывают СЕЙЧАС:</h2>
            <ol style="margin: 20px;">
                <li><strong>ПОЛОЖИТЕ ТРУБКУ</strong> — это ваше право.</li>
                <li><strong>НЕ ПЕРЕЗВАНИВАЙТЕ</strong> на тот же номер.</li>
                <li><strong>РАССКАЖИТЕ БЛИЗКИМ.</strong> Мошенники боятся огласки.</li>
            </ol>
        </div>

        <h3 style="margin-top:40px;">💳 Если вы уже перевели деньги:</h3>
        <div class="card">
            <p>1. <strong>Позвоните в банк</strong> и заблокируйте карту (номер на обороте).</p>
            <p>2. <strong>Позвоните в полицию:</strong> 102 или 112.</p>
            <p>3. <strong>Смените пароли</strong> на Госуслугах и в банках.</p>
        </div>

        <h3 style="margin-top:40px;">📞 Экстренные контакты:</h3>
        <table class="contact-table">
            <tr><th>Организация</th><th>Номер</th></tr>
            <tr><td>Полиция</td><td>112</td></tr>
            <tr><td>Банк России</td><td>8-800-300-30-00</td></tr>
            <tr><td>Госуслуги</td><td>8-800-100-70-10</td></tr>
        </table>
    </div>
</section>

<footer>
    <div class="container">
        <h3>🛡️ КиберЩит — 2026</h3>
        <p>Индивидуальный итоговый проект | Лещенко К.А. | 10-3 класс</p>
        <p style="font-size: 0.8rem; margin-top: 10px;">Источники: МВД РФ, Банк России, ВЦИОМ, Д. Канеман, Р. Чалдини</p>
    </div>
</footer>

<a href="tel:112" class="sos-float">🆘 SOS 112</a>

<script>
    function showPage(id) {
        document.querySelectorAll('section').forEach(s => s.classList.remove('active'));
        document.querySelectorAll('nav a').forEach(a => a.classList.remove('active'));
        document.getElementById(id).classList.add('active');
        event.currentTarget.classList.add('active');
        window.scrollTo(0,0);
    }

    function toggleSenior() { document.body.classList.toggle('senior-mode'); }

    const questions = [
        "Вам позвонили или написали ПЕРВЫМИ?",
        "Вас ПУГАЮТ или СРОЧНО торопят?",
        "Просят сохранить разговор В ТАЙНЕ?",
        "Просят КОД из SMS или данные карты?",
        "Просят ПЕРЕВЕСТИ деньги на другой счет?"
    ];

    const quizList = document.getElementById('quiz-list');
    let answers = new Array(questions.length).fill(null);

    questions.forEach((q, i) => {
        const item = document.createElement('div');
        item.className = 'quiz-item';
        item.innerHTML = `<span>${q}</span><div class="quiz-btn-group"><button class="tgl-btn yes" onclick="setAns(${i},true,this)">Да</button><button class="tgl-btn no" onclick="setAns(${i},false,this)">Нет</button></div>`;
        quizList.appendChild(item);
    });

    function setAns(i, v, b) {
        b.parentElement.querySelectorAll('.tgl-btn').forEach(btn => btn.classList.remove('active'));
        b.classList.add('active');
        answers[i] = v;
    }

    function processQuiz() {
        const score = answers.filter(a => a === true).length;
        const res = document.getElementById('quiz-result');
        res.style.display = 'block';
        if (score >= 3) { res.style.background = '#fecaca'; res.innerHTML = "<h3>🚨 МОШЕННИКИ!</h3><p>Положите трубку немедленно.</p>"; }
        else if (score >= 1) { res.style.background = '#fef3c7'; res.innerHTML = "<h3>⚠️ ПОДОЗРИТЕЛЬНО</h3><p>Проверьте информацию сами.</p>"; }
        else { res.style.background = '#d1fae5'; res.innerHTML = "<h3>✅ БЕЗОПАСНО</h3><p>Но будьте бдительны.</p>"; }
    }

    const obs = new IntersectionObserver((es) => { es.forEach(e => { if(e.isIntersecting) e.target.classList.add('active'); }); });
    document.querySelectorAll('.reveal').forEach(el => obs.observe(el));
</script>
</body>
</html>
