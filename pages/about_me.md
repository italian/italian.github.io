<head>
    <link rel="stylesheet" href="../styles/main.css">
</head>
<body>

<nav class="navbar">
    <a href="https://italian.github.io">Home</a>
    <a href="github_stats.html">My GitHub Stats</a>
    <a href="about_me.html" style="background-color: #dda; color: black;">About Me</a>
    <div class="navbar-right">
        <select id="language-select">
            <option value="en">English</option>
            <option value="ru">Русский</option>
        </select>
    </div>
</nav>
<main>
    <h2>About Me</h2>
    <p id="experience">
        Experienced design engineer with over 13 years of experience in heavy electrical engineering. I specialise in the design and retrofit of high voltage induction motors from 100kW to 2MW.
    </p>
    <p id="skills">
        Professional skills include competences from technical calculations and design to project management and team co-ordination.
    </p>
    <p id="software">
        I have in-depth knowledge of CAD software such as Creo Elements/Pro, T-flex. I also have significant experience with Mathcad for technical calculations.
    </p>
    <p id="programming">
        I actively apply my programming skills in C#, C and Python to automate workflows and develop customised solutions.
    </p>
    <p id="education">
        I am interested in new technologies and am constantly educating myself. I am actively studying machine learning.
    </p>
    <p id="goal">
        My goal is to use my skills and knowledge to develop innovative products and solutions in the field of artificial intelligence.
    </p>
</main>
</body>

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
        fetch(`../translations/${lang}.json`)
       .then(response => response.json())
       .then(translations => {
                document.querySelector('.navbar a[href="https://italian.github.io"]').textContent = translations.home;
                document.querySelector('.navbar a[href="github_stats.html"]').textContent = translations.myGithubStats;
                document.querySelector('.navbar a[href="about_me.html"]').textContent = translations.aboutMe;
                document.querySelector('h2').textContent = translations.aboutMe;

                document.querySelector('#experience').textContent = translations.experience;

                document.querySelector('#skills').textContent = translations.skills;

                document.querySelector('#software').textContent = translations.software;

                document.querySelector('#programming').textContent = translations.programming;

                document.querySelector('#education').textContent = translations.education;

                document.querySelector('#goal').textContent = translations.goal;

                // Добавьте аналогичные строки для других элементов, которые нужно перевести
            });
    }

    // Загружаем переводы по умолчанию при первой загрузке страницы
    loadTranslations(select.value);
});
</script>