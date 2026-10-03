<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>StudyBloom — Student Planner</title>
<style>
:root {
  --pink: #f3a6c8;
  --pink-dark: #d85d96;
  --pink-light: #fff0f6;
  --white: #ffffff;
  --text: #70465a;
  --green: #8bc9a4;
  --yellow: #f5cf7b;
  --purple: #c3a4ed;
  --border: #f5d5e4;
}
* { box-sizing: border-box; }
body {
  margin: 0;
  font-family: "Segoe UI", sans-serif;
  color: var(--text);
  background: linear-gradient(135deg, #fff7fb, #ffeaf3);
  min-height: 100vh;
}
button, input, select, textarea { font: inherit; }
button { cursor: pointer; }
header {
  padding: 25px 6%;
  background: rgba(255,255,255,.92);
  border-bottom: 2px solid var(--border);
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 15px;
  flex-wrap: wrap;
}
.logo { display: flex; align-items: center; gap: 12px; }
.logo-icon {
  width: 50px; height: 50px;
  border-radius: 16px;
  background: var(--pink-light);
  display: grid; place-items: center;
  font-size: 28px;
}
.logo h1 { margin: 0; font-size: 24px; color: var(--pink-dark); }
.logo p { margin: 4px 0 0; font-size: 12px; }
.header-date { font-size: 14px; font-weight: 600; }
.container { max-width: 1250px; margin: auto; padding: 25px 20px 50px; }
.hero {
  padding: 30px;
  border-radius: 25px;
  background: linear-gradient(120deg, #f8c5dc, #fff0f6, #ffffff);
  border: 1px solid var(--border);
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 20px;
  flex-wrap: wrap;
  position: relative;
  overflow: hidden;
}
.hero h2 { margin: 0 0 10px; font-size: 28px; color: #bd5284; }
.hero p { margin: 0; line-height: 1.7; }
.hero-flower { font-size: 70px; }
.stats {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 15px;
  margin: 22px 0;
}
.stat, .panel {
  background: var(--white);
  border: 1px solid var(--border);
  border-radius: 18px;
  padding: 20px;
  box-shadow: 0 5px 18px #d98ab01a;
}
.stat small { color: #a47b8f; }
.stat strong { display: block; font-size: 28px; margin-top: 8px; }
.stat-icon { float: right; font-size: 25px; }
.layout { display: grid; grid-template-columns: 1fr 1.7fr; gap: 20px; }
.panel h3 { margin: 0 0 18px; color: #bd5284; }
.field { margin-bottom: 14px; }
.field label { display: block; font-weight: 600; font-size: 13px; margin-bottom: 7px; }
input, select, textarea {
  width: 100%; padding: 11px 12px;
  border: 1px solid var(--border);
  border-radius: 10px;
  background: #fffafd; color: var(--text);
  outline: none;
}
input:focus, select:focus, textarea:focus {
  border-color: var(--pink-dark);
  box-shadow: 0 0 0 3px #f3a6c833;
}
textarea { min-height: 85px; resize: vertical; }
.btn {
  padding: 10px 15px; border: 0; border-radius: 10px;
  background: var(--pink); color: #713b55; font-weight: 700;
}
.btn:hover { filter: brightness(.97); }
.btn-primary { background: var(--pink-dark); color: white; }
.btn-danger { background: #ffe4e9; color: #b93857; }
.btn-green { background: #e0f5e7; color: #35794c; }
.btn-purple { background: #eee5ff; color: #7653ad; }
.btn-small { padding: 7px 10px; font-size: 12px; }
.task-toolbar { display: flex; gap: 10px; flex-wrap: wrap; margin-bottom: 15px; }
.task-toolbar input { flex: 1; min-width: 150px; }
.task-list { display: grid; gap: 12px; }
.task {
  border: 1px solid var(--border);
  border-radius: 14px;
  padding: 15px;
  background: #fffafd;
}
.task-top { display: flex; justify-content: space-between; gap: 12px; }
.task h4 { margin: 0 0 7px; font-size: 16px; overflow-wrap: anywhere; }
.task p { margin: 5px 0; font-size: 13px; line-height: 1.5; overflow-wrap: anywhere; }
.task-meta { display: flex; flex-wrap: wrap; gap: 7px; margin: 10px 0; }
.badge {
  display: inline-block; border-radius: 20px;
  padding: 5px 9px; font-size: 11px; font-weight: 700;
}
.status-belum { background: #ffe5e9; color: #bb4e65; }
.status-proses { background: #fff0c9; color: #98701c; }
.status-selesai { background: #dcf5e4; color: #35794c; }
.priority { background: #f1e7ff; color: #8058ae; }
.progress-wrap { height: 8px; background: #f8e5ee; border-radius: 10px; overflow: hidden; margin: 15px 0 7px; }
.progress-bar { height: 100%; background: linear-gradient(90deg, #f3a6c8, #d85d96); transition: width .3s; }
.task-actions { display: flex; gap: 7px; flex-wrap: wrap; margin-top: 12px; }
.empty { padding: 30px 10px; text-align: center; color: #b18b9d; }
.section-title { margin: 28px 0 15px; color: #bd5284; }
.footer { text-align: center; padding: 25px; color: #ad8498; font-size: 12px; }
.sakura { color: #e78ab3; }
@media(max-width:850px) {
  .layout { grid-template-columns: 1fr; }
  .stats { grid-template-columns: repeat(2, 1fr); }
}
@media(max-width:480px) {
  header { padding: 18px; }
  .logo h1 { font-size: 20px; }
  .container { padding: 15px 12px 30px; }
  .hero { padding: 22px; }
  .hero h2 { font-size: 23px; }
  .hero-flower { font-size: 45px; }
  .stats { gap: 9px; }
  .stat { padding: 14px; }
  .stat strong { font-size: 23px; }
  .panel { padding: 15px; }
}
</style>
</head>
<body>

<header>
  <div class="logo">
    <div class="logo-icon">🌸</div>
    <div>
      <h1>StudyBloom</h1>
      <p>Student Planner · Grow with your goals</p>
    </div>
  </div>
  <div class="header-date" id="today"></div>
</header>

<main class="container">
  <section class="hero">
    <div>
      <h2>Selamat datang di StudyBloom! 🌷</h2>
      <p>Atur tugasmu, pantau progres belajar, dan capai tujuanmu.<br>
      Sedikit demi sedikit, kamu akan terus berkembang.</p>
    </div>
    <div class="hero-flower">🌸</div>
  </section>

  <section class="stats">
    <div class="stat">
      <span class="stat-icon">📚</span>
      <small>Total Tugas</small>
      <strong id="total">0</strong>
    </div>
    <div class="stat">
      <span class="stat-icon">📝</span>
      <small>Belum Mengerjakan</small>
      <strong id="belum">0</strong>
    </div>
    <div class="stat">
      <span class="stat-icon">🌷</span>
      <small>Sedang Mengerjakan</small>
      <strong id="proses">0</strong>
    </div>
    <div class="stat">
      <span class="stat-icon">🌟</span>
      <small>Sudah Selesai</small>
      <strong id="selesai">0</strong>
    </div>
  </section>

  <section class="panel">
    <h3>🌸 Progres Keseluruhan</h3>
    <div style="display:flex;justify-content:space-between;gap:10px">
      <span>Persentase tugas selesai</span>
      <strong id="percentage">0%</strong>
    </div>
    <div class="progress-wrap">
      <div class="progress-bar" id="overallBar" style="width:0%"></div>
    </div>
    <p id="progressText" style="font-size:13px">Ayo mulai langkah pertamamu!</p>
  </section>

  <h2 class="section-title">🌷 Ruang Belajarku</h2>

  <section class="layout">
    <div class="panel">
      <h3 id="formTitle">✿ Tambahkan Tugas</h3>
      <form id="taskForm">
        <input type="hidden" id="taskId">

        <div class="field">
          <label for="taskName">Nama Tugas *</label>
          <input id="taskName" required placeholder="Contoh: Membuat rangkuman">
        </div>

        <div class="field">
          <label for="subject">Mata Pelajaran *</label>
          <input id="subject" required placeholder="Contoh: Matematika">
        </div>

        <div class="field">
          <label for="deadline">Tanggal Pengumpulan</label>
          <input type="date" id="deadline">
        </div>

        <div class="field">
          <label for="priority">Prioritas</label>
          <select id="priority">
            <option value="Biasa">Biasa</option>
            <option value="Penting">Penting</option>
            <option value="Sangat Penting">Sangat Penting</option>
          </select>
        </div>

        <div class="field">
          <label for="status">Status Pengerjaan</label>
          <select id="status">
            <option value="Belum Mengerjakan">Belum Mengerjakan</option>
            <option value="Sedang Mengerjakan">Sedang Mengerjakan</option>
            <option value="Sudah Selesai">Sudah Selesai</option>
          </select>
        </div>

        <div class="field">
          <label for="taskProgress">Persentase Pengerjaan: <span id="progressValue">0</span>%</label>
          <input type="range" id="taskProgress" min="0" max="100" step="5" value="0">
        </div>

        <div class="field">
          <label for="notes">Catatan Tugas</label>
          <textarea id="notes" placeholder="Tulis catatan atau detail tugas..."></textarea>
        </div>

        <button class="btn btn-primary" type="submit" id="submitBtn" style="width:100%">
          ＋ Simpan Tugas
        </button>
        <button class="btn" type="button" id="cancelEdit" style="width:100%;margin-top:8px;display:none">
          Batal Mengedit
        </button>
      </form>
    </div>

    <div class="panel">
      <h3>🌸 Daftar Tugas</h3>

      <div class="task-toolbar">
        <input type="search" id="search" placeholder="Cari nama tugas atau pelajaran...">
        <select id="filterStatus" style="max-width:200px">
          <option value="Semua">Semua Status</option>
          <option value="Belum Mengerjakan">Belum Mengerjakan</option>
          <option value="Sedang Mengerjakan">Sedang Mengerjakan</option>
          <option value="Sudah Selesai">Sudah Selesai</option>
        </select>
      </div>

      <div class="task-toolbar">
        <button class="btn" type="button" id="exportBtn">⬇ Ekspor Data</button>
        <button class="btn" type="button" id="importBtn">⬆ Impor Data</button>
        <input type="file" id="importFile" accept=".json,application/json" hidden>
      </div>

      <div id="taskList" class="task-list"></div>
    </div>
  </section>

  <div class="footer">
    🌸 StudyBloom Student Planner · Dibuat dengan cinta untuk perjalanan belajarmu 🌸
  </div>
</main>

<script>
const STORAGE_KEY = "studybloom_tasks_v1";
let tasks = [];
let editingId = null;

const $ = id => document.getElementById(id);

function loadTasks() {
  try {
    const saved = localStorage.getItem(STORAGE_KEY);
    const parsed = saved ? JSON.parse(saved) : [];
    tasks = Array.isArray(parsed) ? parsed : [];
  } catch (error) {
    tasks = [];
  }
}

function saveTasks() {
  try {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(tasks));
  } catch (error) {
    alert("Data tidak dapat disimpan. Periksa ruang penyimpanan browser.");
  }
}

function escapeHTML(value) {
  return String(value ?? "").replace(/[&<>"']/g, char => ({
    "&": "&amp;",
    "<": "&lt;",
    ">": "&gt;",
    '"': "&quot;",
    "'": "&#039;"
  })[char]);
}

function normalizeProgress(task) {
  let progress = Number(task.progress) || 0;
  if (task.status === "Sudah Selesai") return 100;
  if (task.status === "Belum Mengerjakan") return 0;
  return Math.max(0, Math.min(100, progress));
}

function statusClass(status) {
  if (status === "Sudah Selesai") return "status-selesai";
  if (status === "Sedang Mengerjakan") return "status-proses";
  return "status-belum";
}

function updateDate() {
  $("today").textContent = new Date().toLocaleDateString("id-ID", {
    weekday: "long",
    day: "numeric",
    month: "long",
    year: "numeric"
  });
}

function updateStats() {
  const total = tasks.length;
  const belum = tasks.filter(t => t.status === "Belum Mengerjakan").length;
  const proses = tasks.filter(t => t.status === "Sedang Mengerjakan").length;
  const selesai = tasks.filter(t => t.status === "Sudah Selesai").length;
  const percentage = total ? Math.round(selesai / total * 100) : 0;

  $("total").textContent = total;
  $("belum").textContent = belum;
  $("proses").textContent = proses;
  $("selesai").textContent = selesai;
  $("percentage").textContent = percentage + "%";
  $("overallBar").style.width = percentage + "%";

  $("progressText").textContent = total === 0
    ? "Ayo tambahkan tugas pertamamu! 🌸"
    : percentage === 100
      ? "Hebat! Semua tugas sudah selesai. Kamu luar biasa! 🌟"
      : `${selesai} dari ${total} tugas sudah selesai. Tetap semangat! 🌷`;
}

function renderTasks() {
  const query = $("search").value.trim().toLowerCase();
  const filter = $("filterStatus").value;

  const filtered = tasks.filter(task => {
    const matchesSearch =
      String(task.name || "").toLowerCase().includes(query) ||
      String(task.subject || "").toLowerCase().includes(query) ||
      String(task.notes || "").toLowerCase().includes(query);

    return matchesSearch &&
      (filter === "Semua" || task.status === filter);
  });

  if (filtered.length === 0) {
    $("taskList").innerHTML = `
      <div class="empty">
        <div style="font-size:42px">🌸</div>
        <p>Belum ada tugas yang cocok.</p>
        <small>Tambahkan tugas baru melalui formulir.</small>
      </div>`;
    updateStats();
    return;
  }

  $("taskList").innerHTML = filtered.map(task => {
    const progress = normalizeProgress(task);
    const deadline = task.deadline
      ? new Date(task.deadline + "T00:00:00").toLocaleDateString("id-ID", {
          day: "numeric", month: "short", year: "numeric"
        })
      : "Belum ditentukan";

    return `
      <article class="task">
        <div class="task-top">
          <div>
            <h4>${escapeHTML(task.name)}</h4>
            <p>📚 ${escapeHTML(task.subject)}</p>
          </div>
          <span class="sakura">🌸</span>
        </div>

        <div class="task-meta">
          <span class="badge ${statusClass(task.status)}">
            ${escapeHTML(task.status)}
          </span>
          <span class="badge priority">
            ${escapeHTML(task.priority || "Biasa")}
          </span>
        </div>

        <p>📅 Tenggat: ${escapeHTML(deadline)}</p>
        ${task.notes ? `<p>📝 ${escapeHTML(task.notes)}</p>` : ""}

        <div style="display:flex;justify-content:space-between;gap:10px;font-size:12px">
          <span>Progres pengerjaan</span>
          <strong>${progress}%</strong>
        </div>
        <div class="progress-wrap">
          <div class="progress-bar" style="width:${progress}%"></div>
        </div>

        <div class="task-actions">
          <button class="btn btn-small" data-action="edit" data-id="${escapeHTML(task.id)}">✏️ Edit</button>
          <button class="btn btn-small btn-purple" data-action="status" data-id="${escapeHTML(task.id)}">🔄 Ubah Status</button>
          <button class="btn btn-small btn-danger" data-action="delete" data-id="${escapeHTML(task.id)}">🗑 Hapus</button>
        </div>
      </article>`;
  }).join("");

  updateStats();
}

function resetForm() {
  $("taskForm").reset();
  $("taskId").value = "";
  $("taskProgress").value = 0;
  $("progressValue").textContent = "0";
  $("formTitle").textContent = "✿ Tambahkan Tugas";
  $("submitBtn").textContent = "＋ Simpan Tugas";
  $("cancelEdit").style.display = "none";
  editingId = null;
}

$("taskProgress").addEventListener("input", () => {
  $("progressValue").textContent = $("taskProgress").value;
});

$("status").addEventListener("change", () => {
  if ($("status").value === "Sudah Selesai") {
    $("taskProgress").value = 100;
  } else if ($("status").value === "Belum Mengerjakan") {
    $("taskProgress").value = 0;
  }
  $("progressValue").textContent = $("taskProgress").value;
});

$("taskForm").addEventListener("submit", event => {
  event.preventDefault();

  const name = $("taskName").value.trim();
  const subject = $("subject").value.trim();
  let status = $("status").value;
  let progress = Number($("taskProgress").value);

  if (!name || !subject) {
    alert("Nama tugas dan mata pelajaran wajib diisi.");
    return;
  }

  if (status === "Sudah Selesai") progress = 100;
  if (status === "Belum Mengerjakan") progress = 0;

  if (progress === 100) status = "Sudah Selesai";
  else if (progress > 0) status = "Sedang Mengerjakan";
  else status = "Belum Mengerjakan";

  const data = {
    id: editingId || (crypto.randomUUID
      ? crypto.randomUUID()
      : String(Date.now()) + Math.random()),
    name,
    subject,
    deadline: $("deadline").value,
    priority: $("priority").value,
    status,
    progress,
    notes: $("notes").value.trim(),
    updatedAt: new Date().toISOString()
  };

  if (editingId) {
    const index = tasks.findIndex(t => t.id === editingId);
    if (index !== -1) tasks[index] = data;
  } else {
    tasks.unshift(data);
  }

  saveTasks();
  resetForm();
  renderTasks();
});

$("cancelEdit").addEventListener("click", resetForm);
$("search").addEventListener("input", renderTasks);
$("filterStatus").addEventListener("change", renderTasks);

$("taskList").addEventListener("click", event => {
  const button = event.target.closest("button[data-action]");
  if (!button) return;

  const task = tasks.find(t => t.id === button.dataset.id);
  if (!task) return;

  const action = button.dataset.action;

  if (action === "edit") {
    editingId = task.id;
    $("taskId").value = task.id;
    $("taskName").value = task.name || "";
    $("subject").value = task.subject || "";
    $("deadline").value = task.deadline || "";
    $("priority").value = task.priority || "Biasa";
    $("status").value = task.status || "Belum Mengerjakan";
    $("taskProgress").value = normalizeProgress(task);
    $("progressValue").textContent = normalizeProgress(task);
    $("notes").value = task.notes || "";
    $("formTitle").textContent = "✿ Edit Tugas";
    $("submitBtn").textContent = "💾 Simpan Perubahan";
    $("cancelEdit").style.display = "block";
    $("taskName").focus();
    window.scrollTo({ top: 0, behavior: "smooth" });
  }

  if (action === "status") {
    const options = [
      "Belum Mengerjakan",
      "Sedang Mengerjakan",
      "Sudah Selesai"
    ];
    const currentIndex = options.indexOf(task.status);
    task.status = options[(currentIndex + 1) % options.length];
    task.progress = task.status === "Sudah Selesai"
      ? 100
      : task.status === "Belum Mengerjakan" ? 0 : 50;
    task.updatedAt = new Date().toISOString();
    saveTasks();
    renderTasks();
  }

  if (action === "delete") {
    if (confirm(`Yakin ingin menghapus tugas "${task.name}"?`)) {
      tasks = tasks.filter(t => t.id !== task.id);
      if (editingId === task.id) resetForm();
      saveTasks();
      renderTasks();
    }
  }
});

$("exportBtn").addEventListener("click", () => {
  const blob = new Blob(
    [JSON.stringify(tasks, null, 2)],
    { type: "application/json" }
  );
  const url = URL.createObjectURL(blob);
  const link = document.createElement("a");
  link.href = url;
  link.download = "StudyBloom_Tugas.json";
  document.body.appendChild(link);
  link.click();
  link
