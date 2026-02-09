<!DOCTYPE html>
<html lang="ar" dir="rtl">

<head>
    <meta charset="UTF-8">
    <title>عالم ال PC</title>
    <style>
        body {
            margin: 0;
            font-family: Tahoma;
            background: #0f172a;
            color: #fff
        }

        header {
            background: linear-gradient(90deg, #2563eb, #7c3aed);
            padding: 20px;
            text-align: center
        }

        nav {
            background: #020617;
            padding: 10px;
            text-align: center
        }

        nav input,
        nav button {
            padding: 8px;
            border-radius: 6px;
            border: none;
            margin: 5px
        }

        nav button {
            cursor: pointer;
            background: #2563eb;
            color: white
        }

        .about {
            padding: 20px;
            text-align: center;
            background: #020617
        }

        .container {
            padding: 30px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px
        }

        .card {
            background: #020617;
            border-radius: 12px;
            padding: 20px;
            box-shadow: 0 0 10px rgba(0, 0, 0, .6);
            transition: .3s
        }

        .card:hover {
            transform: translateY(-5px)
        }

        .btn {
            display: inline-block;
            margin-top: 10px;
            padding: 8px 15px;
            background: #2563eb;
            color: #fff;
            text-decoration: none;
            border-radius: 8px
        }

        .rating span {
            cursor: pointer;
            font-size: 20px;
            color: #64748b
        }

        .rating .active {
            color: gold
        }
    </style>
</head>

<body>

    <header>
        <h1>🌍 عالم ال PC</h1>
        <p>مركزك الشامل لكل ما يخص الكمبيوتر</p>
    </header>

    <div class="about">
        <h2>نبذة عن الموقع</h2>
        <p>عالم ال PC هو موقع عربي متخصص في توفير أفضل ألعاب الكمبيوتر، البرامج الضرورية، ونسخ الويندوز المحدثة مع روابط
            مباشرة وشروحات مبسطة للمستخدمين.</p>
    </div>

    <nav>
        <input type="text" id="search" placeholder="ابحث هنا">
        <button onclick="filterType('all')">الكل</button>
        <button onclick="filterType('لعبة')">الألعاب</button>
        <button onclick="filterType('برنامج')">البرامج</button>
        <button onclick="filterType('ويندوز')">الويندوز</button>
    </nav>

    <section class="container" id="list"></section>

    <script>
        const data = [
            { name: "GTA V", type: "لعبة", desc: "عالم مفتوح", link: "#" },
            { name: "FIFA 24", type: "لعبة", desc: "كرة قدم", link: "#" },
            { name: "Cyberpunk 2077", type: "لعبة", desc: "RPG مستقبلية", link: "#" },

            { name: "Photoshop", type: "برنامج", desc: "تعديل الصور", link: "#" },
            { name: "WinRAR", type: "برنامج", desc: "ضغط الملفات", link: "#" },
            { name: "VLC Player", type: "برنامج", desc: "مشغل فيديو", link: "#" },

            { name: "Windows 7", type: "ويندوز", desc: "نسخة خفيفة ومستقرة", link: "#" },
            { name: "Windows 8", type: "ويندوز", desc: "واجهة مختلفة", link: "#" },
            { name: "Windows 8.1", type: "ويندوز", desc: "تحسينات على 8", link: "#" },
            { name: "Windows 10", type: "ويندوز", desc: "الأكثر استخداماً", link: "#" },
            { name: "Windows 11", type: "ويندوز", desc: "أحدث نسخة", link: "#" }
        ];

        let currentData = data;
        const list = document.getElementById("list");

        function render(items) {
            list.innerHTML = "";
            items.forEach((item, i) => {
                const div = document.createElement("div");
                div.className = "card";
                div.innerHTML = `
      <h3>${item.name}</h3>
      <p>${item.desc}</p>
      <small>${item.type}</small><br>
      <a href="${item.link}" class="btn">تحميل</a>
      <div class="rating">
        <span>★</span><span>★</span><span>★</span><span>★</span><span>★</span>
      </div>`;
                list.appendChild(div);
            });
        }

        render(data);

        search.onkeyup = () => {
            const v = search.value.toLowerCase();
            render(currentData.filter(i => i.name.toLowerCase().includes(v)));
        }

        function filterType(type) {
            if (type === 'all') {
                currentData = data;
            } else {
                currentData = data.filter(i => i.type === type);
            }
            render(currentData);
        }

        list.onclick = (e) => {
            if (e.target.tagName === 'SPAN') {
                const stars = e.target.parentElement.children;
                for (let i = 0; i < stars.length; i++)stars[i].classList.remove('active');
                for (let i = 0; i <= Array.from(stars).indexOf(e.target); i++)stars[i].classList.add('active');
            }
        }
    </script>

</body>

</html>
