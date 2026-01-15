<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Website Study | Educational Platform</title>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #00005D;
  line-height: 1.6;
}

a {
  text-decoration: none;
  color: white;
}

/* ================= HEADER ================= */
header {
  background: url('75e06170e12c918187a64335c0a99d42(1).jpg') center/cover fixed;
  padding: 1.2rem;
  color: white;
}

nav {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  margin-top: 0.5rem;
}

nav a:hover {
  text-decoration: underline;
}

/* ================= MAIN ================= */
main {
  max-width: 1100px;
  margin: auto;
  padding: 1.5rem;
}

section {
  background: white;
  padding: 1.2rem;
  margin-bottom: 1.5rem;
  border-radius: 8px;
}

/* ================= COLLAPSIBLE ================= */
.section-header {
  display: flex;
  justify-content: space-between;
  cursor: pointer;
  background: #eaf2f8;
  padding: 0.8rem;
  border-radius: 6px;
  font-weight: bold;
  user-select: none;
}

.section-header:hover {
  background: #d6eaf8;
}

.section-content {
  display: none;
  margin-top: 1rem;
}

.section-content.active {
  display: block;
}

/* ================= EDITOR ================= */
.editor {
  display: grid;
  gap: 1rem;
}

textarea {
  width: 100%;
  height: 220px;
  font-family: monospace;
  padding: 0.7rem;
}

iframe {
  width: 100%;
  height: 220px;
  border: 1px solid #ccc;
  background: white;
}

button {
  background: #0a3d62;
  color: white;
  border: none;
  padding: 0.6rem 1rem;
  border-radius: 6px;
  cursor: pointer;
}

button:hover {
  background: #07508a;
}

/* ================= SEARCH ================= */
.search-bar {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.search-bar input {
  flex: 1;
  padding: 0.5rem;
}

#lessonList li {
  cursor: pointer;
  padding: 0.4rem;
}

#lessonList li:hover {
  background: #eaf2f8;
}

/* ================= RESPONSIVE ================= */
@media (min-width: 768px) {
  .editor {
    grid-template-columns: 1fr 1fr;
  }
}

/* ================= FOOTER ================= */
footer {
  background: #0a3d62;
  color: white;
  text-align: center;
  padding: 1rem;
}
</style>
</head>

<body>

<header>
  <h1>Website Study</h1>
  <nav>
    <a href="#home">Home</a>
    <a href="#about">About</a>
    <a href="#services">Services</a>
    <a href="#tutorial">Code Tutorial</a>
    <a href="#learn">Learn Code</a>
  </nav>
</header>

<main>

<section id="home">
  <div class="section-header" onclick="toggleSection(this)">
    <span>Welcome</span><span>+</span>
  </div>
  <div class="section-content">
    <p>
      Website Study is an educational platform designed for Grade 11 students
      to learn HTML, CSS, JavaScript, C#, and Java through hands-on practice.
    </p>
  </div>
</section>

<section id="about">
  <div class="section-header" onclick="toggleSection(this)">
    <span>About Us</span><span>+</span>
  </div>
  <div class="section-content">
    <p>
      A self-paced learning platform focused on real coding experience.
    </p>
  </div>
</section>

<section id="services">
  <div class="section-header" onclick="toggleSection(this)">
    <span>Services</span><span>+</span>
  </div>
  <div class="section-content">
    <ul>
      <li>Web Development Fundamentals</li>
      <li>Mobile-First Design</li>
      <li>Live Coding Practice</li>
      <li>Beginner-Friendly Lessons</li>
    </ul>
  </div>
</section>

<section id="tutorial">
  <div class="section-header" onclick="toggleSection(this)">
    <span>Code Tutorial (Live Editor)</span><span>+</span>
  </div>

  <div class="section-content">

    <div id="languageInfo" style="background:#f4f6f7;padding:1rem;border-radius:6px;">
      <h3 id="langTitle">Select a Language</h3>
      <p id="langDescription"></p>
      <strong>Uses:</strong>
      <ul id="langUses"></ul>
      <strong>Steps:</strong>
      <ol id="langSteps"></ol>
    </div>

    <div style="margin:1rem 0;">
      <button onclick="loadExample('html')">HTML</button>
      <button onclick="loadExample('css')">CSS</button>
      <button onclick="loadExample('js')">JavaScript</button>
    </div>

    <div class="editor">
      <textarea id="codeInput"></textarea>
      <iframe id="output"></iframe>
    </div>

    <button onclick="runCode()">Run Code</button>
  </div>
</section>

<section id="learn">
  <div class="section-header" onclick="toggleSection(this)">
    <span>Learn Code</span><span>+</span>
  </div>

  <div class="section-content">
    <div class="search-bar">
      <input id="searchInput" placeholder="Search lesson..." />
      <button onclick="searchLessons()">Search</button>
    </div>

    <ul id="lessonList">
      <li onclick="loadLesson('html')">HTML Basics</li>
      <li onclick="loadLesson('css')">CSS Styling</li>
      <li onclick="loadLesson('js')">JavaScript Fundamentals</li>
    </ul>

    <div id="lessonGuide" style="display:none;">
      <h3 id="lessonTitle"></h3>
      <p id="lessonDescription"></p>
      <ol id="lessonSteps"></ol>
    </div>

    <div id="lessonEditor" class="editor" style="display:none;">
      <textarea id="lessonCode"></textarea>
      <iframe id="lessonOutput"></iframe>
    </div>

    <button onclick="runLessonCode()">Run Lesson</button>
  </div>
</section>

</main>

<footer>© 2026 Website Study</footer>

<script>
function toggleSection(header) {
  const content = header.nextElementSibling;
  const icon = header.querySelector("span:last-child");
  content.classList.toggle("active");
  icon.textContent = content.classList.contains("active") ? "−" : "+";
}

const examples = {
  html: "<h1>Hello HTML</h1><p>This is HTML.</p>",
  css: "<style>h1{color:blue}</style><h1>CSS Example</h1>",
  js: "<button onclick=\"alert('Hello!')\">Click Me</button>"
};

const info = {
  html: ["HTML", "Structures web pages", ["Content", "Layout"], ["Tags", "Elements"]],
  css: ["CSS", "Styles pages", ["Colors", "Layout"], ["Selectors", "Properties"]],
  js: ["JavaScript", "Adds interactivity", ["Events", "Logic"], ["Functions", "Events"]]
};

function loadExample(type) {
  codeInput.value = examples[type];
  output.srcdoc = examples[type];
  langTitle.textContent = info[type][0];
  langDescription.textContent = info[type][1];
  langUses.innerHTML = info[type][2].map(i=>`<li>${i}</li>`).join("");
  langSteps.innerHTML = info[type][3].map(i=>`<li>${i}</li>`).join("");
}

function runCode() {
  output.srcdoc = codeInput.value;
}

function loadLesson(type) {
  lessonTitle.textContent = type.toUpperCase() + " Lesson";
  lessonDescription.textContent = "Learn " + type.toUpperCase();
  lessonSteps.innerHTML = "<li>Write</li><li>Run</li>";
  lessonCode.value = examples[type];
  lessonOutput.srcdoc = examples[type];
  lessonGuide.style.display = "block";
  lessonEditor.style.display = "grid";
}

function runLessonCode() {
  lessonOutput.srcdoc = lessonCode.value;
}

function searchLessons() {
  const v = searchInput.value.toLowerCase();
  document.querySelectorAll("#lessonList li").forEach(li=>{
    li.style.display = li.textContent.toLowerCase().includes(v) ? "" : "none";
  });
}
</script>

</body>
</html>
