<head>
    <link rel="stylesheet" href="styles/main.css">
</head>
<body>

<nav class="navbar">
    <a href="https://italian.github.io" style="background-color: #dda; color: black;">Home</a>
    <a href="pages/github_stats.html">My GitHub Stats</a>
    <a href="pages/about_me.html">About Me</a>
    <select id="language-select">
        <option value="en">English</option>
        <option value="ru">Русский</option>
    </select>
</nav>
<main>
    <h1 align="center">ℌ𝔦 𝔱𝔥𝔢𝔯𝔢, ℑ'𝔪 𝔐𝔞𝔵</h1>
    <h3 align="center">Machine learning engineering student,<br>Leading design engineer of induction motors</h3>
</main>
</body>

---

<script>
document.addEventListener('DOMContentLoaded', function() {
    const select = document.getElementById('language-select');

    // Установка выбранного ранее языка при загрузке страницы
    if (localStorage.getItem('selectedLanguage')) {
        select.value = localStorage.getItem('selectedLanguage');
    }

    select.addEventListener('change', function() {
        loadTranslations(this.value);

        // Сохранение выбранного языка в localStorage
        localStorage.setItem('selectedLanguage', this.value);
    });

    function loadTranslations(lang) {
        fetch(`translations/${lang}.json`)
        .then(response => response.json())
        .then(translations => {
            document.querySelector('.navbar a[href="https://italian.github.io"]').textContent = translations.home;
            document.querySelector('.navbar a[href="pages/github_stats.html"]').textContent = translations.myGithubStats;
            document.querySelector('.navbar a[href="pages/about_me.html"]').textContent = translations.aboutMe;
            document.querySelector('h1').textContent = translations.welcomeMessage;

            let descriptionText = translations.description.replace(/\n/g, '<br>');
            document.querySelector('h3').innerHTML = descriptionText;
            // Добавьте аналогичные строки для других элементов, которые нужно перевести
        });
    }

    // Загружаем переводы по умолчанию при первой загрузке страницы
    loadTranslations(select.value);
});
</script>