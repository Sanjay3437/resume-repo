
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:var(--font-sans);color:var(--color-text-primary)}
.wrap{padding:1.5rem 0}
.header{display:flex;align-items:center;justify-content:space-between;margin-bottom:1.5rem}
.header h1{font-size:20px;font-weight:500}
.badge{font-size:11px;padding:3px 10px;border-radius:20px;background:var(--color-background-info);color:var(--color-text-info)}
.tabs{display:flex;gap:0;border:0.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);overflow:hidden;margin-bottom:1.5rem;width:fit-content}
.tab{padding:7px 20px;font-size:13px;cursor:pointer;background:transparent;border:none;color:var(--color-text-secondary);font-family:var(--font-sans)}
.tab.active{background:var(--color-background-secondary);color:var(--color-text-primary);font-weight:500}
.section{margin-bottom:1.25rem}
.section label{display:block;font-size:12px;color:var(--color-text-secondary);margin-bottom:6px;letter-spacing:.02em}
.section textarea{width:100%;min-height:80px;padding:10px 12px;font-size:14px;font-family:var(--font-sans);border:0.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);background:var(--color-background-primary);color:var(--color-text-primary);resize:vertical;line-height:1.6}
.section textarea:focus{outline:none;border-color:var(--color-border-secondary)}
.section input[type=text]{width:100%;padding:9px 12px;font-size:14px;font-family:var(--font-sans);border:0.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);background:var(--color-background-primary);color:var(--color-text-primary)}
.section input:focus{outline:none;border-color:var(--color-border-secondary)}
.row{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.type-toggle{display:flex;gap:8px;flex-wrap:wrap}
.type-btn{padding:5px 14px;font-size:12px;border:0.5px solid var(--color-border-tertiary);border-radius:20px;cursor:pointer;background:transparent;color:var(--color-text-secondary);font-family:var(--font-sans)}
.type-btn.sel{background:var(--color-background-secondary);color:var(--color-text-primary);border-color:var(--color-border-secondary);font-weight:500}
.submit-btn{width:100%;padding:11px;font-size:14px;font-weight:500;border:none;border-radius:var(--border-radius-md);background:var(--color-text-primary);color:var(--color-background-primary);cursor:pointer;font-family:var(--font-sans);margin-top:.5rem}
.submit-btn:hover{opacity:.88}
.empty{text-align:center;padding:3rem 1rem;color:var(--color-text-tertiary);font-size:14px}
.entry-card{border:0.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);padding:1rem 1.25rem;margin-bottom:12px;background:var(--color-background-primary)}
.entry-head{display:flex;align-items:center;justify-content:space-between;margin-bottom:10px}
.entry-date{font-size:13px;font-weight:500}
.entry-type{font-size:11px;padding:3px 10px;border-radius:20px}
.t-support{background:#E1F5EE;color:#0F6E56}
.t-fiot{background:#E6F1FB;color:#185FA5}
.t-general{background:#F1EFE8;color:#5F5E5A}
.entry-section{margin-bottom:8px}
.entry-section-label{font-size:11px;color:var(--color-text-tertiary);text-transform:uppercase;letter-spacing:.05em;margin-bottom:3px}
.entry-section-val{font-size:13px;color:var(--color-text-primary);line-height:1.6}
.no-val{color:var(--color-text-tertiary);font-style:italic}
.entry-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.del-btn{background:none;border:none;cursor:pointer;color:var(--color-text-tertiary);font-size:14px;padding:2px 6px;border-radius:4px}
.del-btn:hover{color:var(--color-text-danger,#c0392b)}
.filter-bar{display:flex;gap:8px;margin-bottom:1rem;flex-wrap:wrap}
.filter-btn{padding:5px 12px;font-size:12px;border:0.5px solid var(--color-border-tertiary);border-radius:20px;cursor:pointer;background:transparent;color:var(--color-text-secondary);font-family:var(--font-sans)}
.filter-btn.active{background:var(--color-background-secondary);color:var(--color-text-primary);font-weight:500}
.export-btn{padding:7px 16px;font-size:13px;border:0.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);cursor:pointer;background:transparent;color:var(--color-text-secondary);font-family:var(--font-sans)}
.export-btn:hover{background:var(--color-background-secondary)}
.stats-row{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-bottom:1.5rem}
.stat-card{background:var(--color-background-secondary);border-radius:var(--border-radius-md);padding:.9rem 1rem;text-align:center}
.stat-num{font-size:22px;font-weight:500}
.stat-lbl{font-size:11px;color:var(--color-text-secondary);margin-top:3px}
.divider{border:none;border-top:0.5px solid var(--color-border-tertiary);margin:1.25rem 0}
</style>
<div class="wrap">
  <div class="header">
    <h1>Daily work log</h1>
    <span class="badge" id="today-badge"></span>
  </div>
  <div class="tabs">
    <button class="tab active" onclick="switchTab('add')">Add entry</button>
    <button class="tab" onclick="switchTab('log')">View log</button>
  </div>

  <div id="tab-add">
    <div class="row">
      <div class="section">
        <label>Date</label>
        <input type="text" id="f-date" placeholder="e.g. 19 Mar 2026" />
      </div>
      <div class="section">
        <label>Day type</label>
        <div class="type-toggle">
          <button class="type-btn sel" onclick="selType(this,'General')">General</button>
          <button class="type-btn" onclick="selType(this,'Client Support')">Client support</button>
          <button class="type-btn" onclick="selType(this,'FIOT Validation')">FIOT validation</button>
        </div>
      </div>
    </div>

    <div class="section">
      <label>Tasks completed</label>
      <textarea id="f-tasks" placeholder="List what you completed today, one per line or briefly described..."></textarea>
    </div>

    <div id="support-section" style="display:none">
      <div class="section">
        <label>Client support details</label>
        <textarea id="f-support" placeholder="Client name, issue raised, action taken, resolution status..."></textarea>
      </div>
    </div>

    <div id="fiot-section" style="display:none">
      <div class="section">
        <label>FIOT app validation details</label>
        <textarea id="f-fiot" placeholder="Module/feature validated, test cases covered, pass/fail status, observations..."></textarea>
      </div>
    </div>

    <div class="section">
      <label>Issues / blockers</label>
      <textarea id="f-blockers" style="min-height:60px" placeholder="Any blockers, pending approvals, or issues faced... (leave blank if none)"></textarea>
    </div>

    <div class="section">
      <label>Tomorrow's plan</label>
      <textarea id="f-plan" style="min-height:60px" placeholder="What do you plan to work on tomorrow?"></textarea>
    </div>

    <button class="submit-btn" onclick="saveEntry()">Save today's entry</button>
  </div>

  <div id="tab-log" style="display:none">
    <div class="stats-row">
      <div class="stat-card"><div class="stat-num" id="s-total">0</div><div class="stat-lbl">Total entries</div></div>
      <div class="stat-card"><div class="stat-num" id="s-support">0</div><div class="stat-lbl">Support days</div></div>
      <div class="stat-card"><div class="stat-num" id="s-fiot">0</div><div class="stat-lbl">FIOT days</div></div>
    </div>
    <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:.75rem">
      <div class="filter-bar" style="margin:0">
        <button class="filter-btn active" onclick="filterLog(this,'all')">All</button>
        <button class="filter-btn" onclick="filterLog(this,'General')">General</button>
        <button class="filter-btn" onclick="filterLog(this,'Client Support')">Support</button>
        <button class="filter-btn" onclick="filterLog(this,'FIOT Validation')">FIOT</button>
      </div>
      <button class="export-btn" onclick="exportLog()">Export ↓</button>
    </div>
    <div id="log-container"></div>
  </div>
</div>

<script>
let entries = JSON.parse(localStorage.getItem('worklog_entries')||'[]');
let currentType = 'General';
let currentFilter = 'all';

function init(){
  const d = new Date();
  document.getElementById('f-date').value = d.toLocaleDateString('en-GB',{day:'numeric',month:'short',year:'numeric'});
  document.getElementById('today-badge').textContent = d.toLocaleDateString('en-GB',{weekday:'short',day:'numeric',month:'short'});
  renderLog();
}

function switchTab(t){
  document.getElementById('tab-add').style.display = t==='add'?'block':'none';
  document.getElementById('tab-log').style.display = t==='log'?'block':'none';
  document.querySelectorAll('.tab').forEach((b,i)=>b.classList.toggle('active',(t==='add'&&i===0)||(t==='log'&&i===1)));
  if(t==='log') renderLog();
}

function selType(btn, type){
  document.querySelectorAll('.type-btn').forEach(b=>b.classList.remove('sel'));
  btn.classList.add('sel');
  currentType = type;
  document.getElementById('support-section').style.display = type==='Client Support'?'block':'none';
  document.getElementById('fiot-section').style.display = type==='FIOT Validation'?'block':'none';
}

function saveEntry(){
  const date = document.getElementById('f-date').value.trim();
  const tasks = document.getElementById('f-tasks').value.trim();
  if(!date||!tasks){alert('Please fill in the date and tasks completed.');return;}
  const entry = {
    id: Date.now(),
    date,
    type: currentType,
    tasks,
    support: document.getElementById('f-support').value.trim(),
    fiot: document.getElementById('f-fiot').value.trim(),
    blockers: document.getElementById('f-blockers').value.trim(),
    plan: document.getElementById('f-plan').value.trim()
  };
  entries.unshift(entry);
  localStorage.setItem('worklog_entries', JSON.stringify(entries));
  ['f-tasks','f-support','f-fiot','f-blockers','f-plan'].forEach(id=>document.getElementById(id).value='');
  switchTab('log');
}

function deleteEntry(id){
  if(!confirm('Delete this entry?')) return;
  entries = entries.filter(e=>e.id!==id);
  localStorage.setItem('worklog_entries', JSON.stringify(entries));
  renderLog();
}

function filterLog(btn, filter){
  currentFilter = filter;
  document.querySelectorAll('.filter-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  renderLog();
}

function renderLog(){
  const filtered = currentFilter==='all'?entries:entries.filter(e=>e.type===currentFilter);
  const total = entries.length;
  const sup = entries.filter(e=>e.type==='Client Support').length;
  const fiot = entries.filter(e=>e.type==='FIOT Validation').length;
  document.getElementById('s-total').textContent = total;
  document.getElementById('s-support').textContent = sup;
  document.getElementById('s-fiot').textContent = fiot;

  const c = document.getElementById('log-container');
  if(!filtered.length){c.innerHTML='<div class="empty">No entries yet. Start adding your daily work log.</div>';return;}
  c.innerHTML = filtered.map(e=>`
    <div class="entry-card">
      <div class="entry-head">
        <span class="entry-date">${e.date}</span>
        <div style="display:flex;align-items:center;gap:8px">
          <span class="entry-type ${e.type==='Client Support'?'t-support':e.type==='FIOT Validation'?'t-fiot':'t-general'}">${e.type}</span>
          <button class="del-btn" onclick="deleteEntry(${e.id})">✕</button>
        </div>
      </div>
      <div class="entry-section">
        <div class="entry-section-label">Tasks completed</div>
        <div class="entry-section-val">${e.tasks.replace(/\n/g,'<br>')}</div>
      </div>
      ${e.support?`<div class="entry-section"><div class="entry-section-label">Client support</div><div class="entry-section-val">${e.support.replace(/\n/g,'<br>')}</div></div>`:''}
      ${e.fiot?`<div class="entry-section"><div class="entry-section-label">FIOT validation</div><div class="entry-section-val">${e.fiot.replace(/\n/g,'<br>')}</div></div>`:''}
      <div class="entry-grid">
        <div class="entry-section">
          <div class="entry-section-label">Issues / blockers</div>
          <div class="entry-section-val">${e.blockers||'<span class="no-val">None</span>'}</div>
        </div>
        <div class="entry-section">
          <div class="entry-section-label">Tomorrow's plan</div>
          <div class="entry-section-val">${e.plan||'<span class="no-val">Not noted</span>'}</div>
        </div>
      </div>
    </div>
  `).join('');
}

function exportLog(){
  const data = currentFilter==='all'?entries:entries.filter(e=>e.type===currentFilter);
  if(!data.length){alert('No entries to export.');return;}
  let txt = 'DAILY WORK LOG\n'+'='.repeat(50)+'\n\n';
  data.forEach(e=>{
    txt += `Date: ${e.date}  |  Type: ${e.type}\n`;
    txt += '-'.repeat(40)+'\n';
    txt += `TASKS COMPLETED:\n${e.tasks}\n\n`;
    if(e.support) txt += `CLIENT SUPPORT:\n${e.support}\n\n`;
    if(e.fiot) txt += `FIOT VALIDATION:\n${e.fiot}\n\n`;
    txt += `ISSUES/BLOCKERS:\n${e.blockers||'None'}\n\n`;
    txt += `TOMORROW'S PLAN:\n${e.plan||'Not noted'}\n\n`;
    txt += '='.repeat(50)+'\n\n';
  });
  const a = document.createElement('a');
  a.href = 'data:text/plain;charset=utf-8,'+encodeURIComponent(txt);
  a.download = 'work_log_export.txt';
  a.click();
}

init();
</script>
