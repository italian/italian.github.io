<head>
    <link rel="stylesheet" href="../styles/main.css">
</head>
<body>

<nav class="navbar">
    <a href="https://italian.github.io">Home</a>
    <a href="github_stats.html" style="background-color: #dda; color: black;">My GitHub Stats</a>
    <a href="about_me.html">About Me</a>
    <select id="language-select">
        <option value="en">English</option>
        <option value="ru">Русский</option>
    </select>
</nav>

<main>
  <div align="center">

    <h2>
      <a href="https://github.com/italian" title="Go to my GitHub profile" id="githubTitle">My GitHub</a>
      <span id="githubLinkText"> stats</span>
    </h2>
    <a href="https://git.io/streak-stats">
      <img align="center" src="https://streak-stats.demolab.com/?user=italian" />
    </a>
    <br><br>
    <a href="https://github.com/ryo-ma/github-profile-trophy">
      <img align="center" src="https://github-profile-trophy.vercel.app/?username=italian&no-bg=false&theme=oldie&column=-1&rank=SECRET,SSS,SS,S,AAA,AA,A,B,C" />
    </a>
    <br><br>
    <a href="https://github.com/anuraghazra/github-readme-stats">
      <img height=200 align="center" src="https://github-readme-stats.vercel.app/api?username=italian&hide=stars,issues&show=reviews,prs_merged,prs_merged_percentage&show_icons=true&theme=swift" />
    </a>
    <a href="https://github.com/anuraghazra/convoychat">
      <img height=200 align="center" src="https://github-readme-stats.vercel.app/api/top-langs/?username=italian" />
    </a>
    <br><br>
    <a href="https://github.com/ashutosh00710/github-readme-activity-graph">
      <img align="center" src="https://github-readme-activity-graph.vercel.app/graph?username=italian&theme=high-contrast&height=380&custom_title=Contribution%20Graph&radius=16" />
    </a>
      
  </div>
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

                // Перевод заголовка и ссылки
                document.querySelector('#githubTitle').textContent = translations.githubTitle;
                document.querySelector('#githubTitle').setAttribute('title', translations.githubTitleTooltip);
                document.querySelector('#githubLinkText').textContent = translations.githubLinkText;
            });
    }

    // Загружаем переводы по умолчанию при первой загрузке страницы
    loadTranslations(select.value);
});
</script>