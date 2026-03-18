[book_to_bill_raci.1.html](https://github.com/user-attachments/files/26090679/book_to_bill_raci.1.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Book to Bill – RACI</title>
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:Arial,sans-serif;font-size:13px;background:#f4f5f7;color:#172b4d;min-height:100vh;display:flex;flex-direction:column}

/* TOPBAR */
.topbar{background:#0052cc;color:#fff;padding:10px 20px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:50;flex-shrink:0}
.brand{font-weight:700;font-size:15px}
.topbar-right{display:flex;align-items:center;gap:8px}
.dot{width:8px;height:8px;border-radius:50%;background:#ffab00;display:none;margin-right:2px}
.tbtn{border:none;border-radius:4px;padding:6px 13px;font-size:12px;font-weight:700;cursor:pointer;display:flex;align-items:center;gap:5px;transition:background .15s}
.tbtn-save{background:#36b37e;color:#fff}.tbtn-save:hover{background:#2da06e}
.tbtn-save:disabled{background:#6b778c;cursor:not-allowed}
.tbtn-log{background:rgba(255,255,255,.15);color:#fff;border:1px solid rgba(255,255,255,.3)}.tbtn-log:hover{background:rgba(255,255,255,.28)}

/* TABS */
.tabs{background:#fff;border-bottom:2px solid #dfe1e6;padding:0 20px;display:flex;gap:0;flex-shrink:0}
.tab{padding:10px 18px;font-size:12px;font-weight:600;color:#6b778c;cursor:pointer;border-bottom:3px solid transparent;margin-bottom:-2px;transition:color .12s,border-color .12s}
.tab:hover{color:#0052cc}
.tab.active{color:#0052cc;border-bottom-color:#0052cc}

/* TOOLBAR */
.toolbar{background:#fff;border-bottom:1px solid #dfe1e6;padding:9px 20px;display:flex;gap:12px;align-items:center;flex-wrap:wrap;flex-shrink:0}
.toolbar label{font-size:11px;color:#6b778c;font-weight:600}
.toolbar select{font-size:12px;padding:5px 8px;border:1.5px solid #dfe1e6;border-radius:4px;background:#fff;color:#172b4d;outline:none}
.toolbar select:focus{border-color:#0052cc}
.edit-hint{font-size:11px;color:#6b778c;font-style:italic}

/* PANELS */
.panel{display:none;flex:1;overflow-y:auto}
.panel.active{display:block}

/* RACI TABLE */
.content{padding:16px 20px}
.page-title{font-size:15px;font-weight:700;margin-bottom:2px}
.page-sub{font-size:11px;color:#6b778c;margin-bottom:12px}
.legend{display:flex;gap:10px;flex-wrap:wrap;margin-bottom:12px;align-items:center}
.leg{display:flex;align-items:center;gap:5px;font-size:11px;color:#6b778c}
.badge{display:inline-flex;align-items:center;justify-content:center;width:28px;height:28px;border-radius:4px;font-weight:700;font-size:11px;user-select:none;transition:transform .1s,opacity .15s;cursor:pointer}
.badge:hover{transform:scale(1.13);box-shadow:0 0 0 2px #0052cc55}
.badge.off{opacity:.15;transform:scale(.88)}
.badge.off:hover{opacity:.35;transform:scale(1.05)}
.r{background:#c0dd97;color:#27500a}.a{background:#b5d4f4;color:#0c447c}
.c{background:#fac775;color:#633806}.i{background:#d3d1c7;color:#444441}
.ra{background:#9fe1cb;color:#085041}
.empty{color:#bbb;font-size:15px;cursor:pointer;padding:4px 8px;border-radius:4px;transition:background .1s}
.empty:hover{background:#f0f4ff}
table{width:100%;border-collapse:collapse;table-layout:fixed;min-width:860px}
th,td{border:1px solid #dfe1e6;padding:6px 7px;vertical-align:middle;text-align:center}
th{font-weight:600;font-size:10px;background:#f4f5f7;color:#6b778c;text-transform:uppercase;letter-spacing:.3px}
th.proc-h{text-align:left}
td.step{text-align:left;font-size:11px;color:#172b4d;padding-left:18px}
.section-row td{background:#ebecf0;font-weight:700;font-size:11px;text-align:left;color:#172b4d;text-transform:uppercase;letter-spacing:.3px}
col.proc{width:24%}col.role{width:9.5%}
tr:hover td:not(.section-row td){background:#f0f4ff}
.section-row:hover td{background:#ebecf0}

/* AUDIT LOG PANEL */
.log-panel{padding:20px}
.log-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:16px;flex-wrap:wrap;gap:10px}
.log-title{font-size:15px;font-weight:700}
.log-controls{display:flex;gap:8px;align-items:center;flex-wrap:wrap}
.log-search{font-size:12px;padding:6px 10px;border:1.5px solid #dfe1e6;border-radius:4px;outline:none;width:200px}
.log-search:focus{border-color:#0052cc}
.btn-csv{background:#0052cc;color:#fff;border:none;border-radius:4px;padding:6px 13px;font-size:12px;font-weight:700;cursor:pointer}
.btn-csv:hover{background:#0065ff}
.btn-clear{background:#fff;color:#de350b;border:1px solid #de350b;border-radius:4px;padding:6px 10px;font-size:12px;font-weight:600;cursor:pointer}
.btn-clear:hover{background:#ffebe6}
.log-empty{text-align:center;color:#6b778c;padding:40px 0;font-size:13px}
.log-table{width:100%;border-collapse:collapse;font-size:12px}
.log-table th{background:#f4f5f7;text-align:left;padding:8px 10px;font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:.4px;color:#6b778c;border-bottom:2px solid #dfe1e6;position:sticky;top:0}
.log-table td{padding:8px 10px;border-bottom:1px solid #f0f0f0;vertical-align:top}
.log-table tr:hover td{background:#f8f9ff}
.val-old{color:#de350b;font-weight:600}.val-new{color:#006644;font-weight:600}
.arrow{color:#6b778c;font-size:11px;margin:0 4px}
.badge-sm{display:inline-block;padding:2px 7px;border-radius:8px;font-size:10px;font-weight:700}
.inactive-tag{background:#f4f5f7;color:#6b778c;font-size:10px;padding:1px 6px;border-radius:6px;margin-left:4px}
.ts{color:#6b778c;font-size:11px}
.stats-bar{display:flex;gap:12px;margin-bottom:16px;flex-wrap:wrap}
.stat{background:#fff;border:1px solid #dfe1e6;border-radius:6px;padding:8px 16px;text-align:center}
.stat-n{font-size:20px;font-weight:700;color:#0052cc}
.stat-l{font-size:10px;color:#6b778c;text-transform:uppercase;letter-spacing:.4px}

/* CELL POPUP */
.popup{display:none;position:fixed;z-index:200;background:#fff;border-radius:8px;box-shadow:0 4px 24px rgba(0,0,0,.22);width:260px;overflow:hidden}
.popup.open{display:block}
.popup-head{background:#0052cc;color:#fff;padding:10px 14px;font-weight:700;font-size:13px;display:flex;justify-content:space-between;align-items:center}
.popup-head button{background:none;border:none;color:#fff;font-size:18px;cursor:pointer;line-height:1}
.popup-body{padding:12px 14px}
.icon-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:10px}
.icon-opt{display:flex;flex-direction:column;align-items:center;gap:4px;cursor:pointer;padding:6px 4px;border-radius:6px;border:2px solid transparent;transition:border .12s}
.icon-opt:hover{border-color:#0052cc55}
.icon-opt.selected{border-color:#0052cc;background:#f0f4ff}
.icon-opt .lbl{font-size:9px;color:#6b778c}
.off-row{display:flex;align-items:center;gap:8px;font-size:12px;color:#172b4d;padding:8px 0;border-top:1px solid #f0f0f0;margin-top:2px;cursor:pointer}
.off-row input[type=checkbox]{width:15px;height:15px;cursor:pointer;accent-color:#0052cc}
.popup-footer{display:flex;gap:6px;padding:10px 14px;border-top:1px solid #f0f0f0;background:#f4f5f7}
.btn-apply{background:#0052cc;color:#fff;border:none;border-radius:4px;padding:6px 14px;font-size:12px;font-weight:700;cursor:pointer;flex:1}
.btn-apply:hover{background:#0065ff}
.btn-cancel2{background:#fff;color:#172b4d;border:1px solid #dfe1e6;border-radius:4px;padding:6px 10px;font-size:12px;cursor:pointer}
.btn-cancel2:hover{background:#ebecf0}

/* MODALS */
.modal-bg{display:none;position:fixed;inset:0;background:rgba(0,0,0,.5);z-index:300;align-items:center;justify-content:center}
.modal-bg.open{display:flex}
.modal{background:#fff;border-radius:8px;box-shadow:0 6px 30px rgba(0,0,0,.2);width:380px;overflow:hidden}
.modal-head{background:#0052cc;color:#fff;padding:14px 18px;font-weight:700;font-size:14px;display:flex;justify-content:space-between;align-items:center}
.modal-head button{background:none;border:none;color:#fff;font-size:18px;cursor:pointer}
.modal-body{padding:20px 18px}
.info-box{font-size:12px;color:#6b778c;margin-bottom:14px;line-height:1.6;background:#f4f5f7;padding:10px 12px;border-radius:6px;border-left:3px solid #0052cc}
.modal-body label{display:block;font-size:11px;font-weight:600;color:#6b778c;text-transform:uppercase;letter-spacing:.5px;margin-bottom:4px;margin-top:10px}
.modal-body input{width:100%;border:1.5px solid #dfe1e6;border-radius:4px;padding:8px 10px;font-size:13px;outline:none}
.modal-body input:focus{border-color:#0052cc}
.login-err{color:#de350b;font-size:12px;margin-top:8px;display:none}
.modal-footer{display:flex;gap:8px;padding:14px 18px;border-top:1px solid #f0f0f0;background:#f4f5f7;justify-content:flex-end}
.btn-confirm{background:#36b37e;color:#fff;border:none;border-radius:4px;padding:8px 20px;font-size:13px;font-weight:700;cursor:pointer}
.btn-confirm:hover{background:#2da06e}
.btn-discard{background:#fff;color:#de350b;border:1px solid #de350b;border-radius:4px;padding:8px 14px;font-size:13px;cursor:pointer}
.btn-discard:hover{background:#ffebe6}
.success-banner{display:none;background:#e3fcef;border:1px solid #abf5d1;color:#006644;padding:12px 14px;border-radius:6px;font-size:13px;font-weight:700;text-align:center}
.users-hint{font-size:11px;color:#6b778c;margin-top:12px;border-top:1px solid #f0f0f0;padding-top:10px;line-height:1.8}
.users-hint b{color:#172b4d}
.rpill{display:inline-block;padding:1px 7px;border-radius:8px;font-size:10px;font-weight:600}
.p-cbm{background:#e3fcef;color:#006644}.p-fbp{background:#deebff;color:#0052cc}.p-adm{background:#fff0b3;color:#974f0c}
</style>
</head>
<body>

<!-- TOPBAR -->
<div class="topbar">
  <div class="brand">Keyloop · Book to Bill RACI</div>
  <div class="topbar-right">
    <div class="dot" id="changesDot" title="Unsaved changes"></div>
    <button class="tbtn tbtn-log" onclick="switchTab('log')">&#128203; Audit Log</button>
    <button class="tbtn tbtn-save" id="btnSave" onclick="openSaveModal()" disabled>&#128190; Save changes</button>
  </div>
</div>

<!-- TABS -->
<div class="tabs">
  <div class="tab active" id="tab-raci" onclick="switchTab('raci')">RACI Table</div>
  <div class="tab" id="tab-log" onclick="switchTab('log')">Audit Log <span id="logCount" style="background:#0052cc;color:#fff;border-radius:8px;padding:1px 7px;font-size:10px;margin-left:4px;display:none">0</span></div>
</div>

<!-- TOOLBAR (RACI only) -->
<div class="toolbar" id="raciToolbar">
  <label>Region / System:</label>
  <select id="sysFilter" onchange="filterTable()">
    <option value="all">All regions</option>
    <option value="kf">UKI — Keyforce / NetSuite</option>
    <option value="rq">Canada — Rapid / QuickBooks</option>
    <option value="css">RoW — CSS / Navision</option>
    <option value="se">Canada — Serti / Billing</option>
  </select>
  <span class="edit-hint">Click any badge to change it · Save changes requires sign-in</span>
</div>

<!-- RACI PANEL -->
<div class="panel active" id="panel-raci">
  <div class="content">
    <div class="page-title">Book to Bill — RACI by system &amp; region</div>
    <div class="page-sub">FBP = Finance Business Partner &nbsp;|&nbsp; CBM = Contract &amp; Billing Management</div>
    <div class="legend">
      <div class="leg"><span class="badge r" style="cursor:default">R</span> Responsible</div>
      <div class="leg"><span class="badge a" style="cursor:default">A</span> Accountable</div>
      <div class="leg"><span class="badge c" style="cursor:default">C</span> Consulted</div>
      <div class="leg"><span class="badge i" style="cursor:default">I</span> Informed</div>
      <div class="leg"><span class="badge ra" style="cursor:default">R/A</span> Resp. &amp; Accountable</div>
    </div>
    <div style="overflow-x:auto">
    <table id="raciTable">
    <colgroup><col class="proc"><col class="role"><col class="role"><col class="role"><col class="role"><col class="role"><col class="role"><col class="role"><col class="role"></colgroup>
    <thead>
    <tr>
      <th class="proc-h" rowspan="3">Process step</th>
      <th colspan="2">Keyforce – NetSuite</th><th colspan="2">Rapid – QuickBooks</th>
      <th colspan="2">CSS – Navision</th><th colspan="2">Serti – Billing</th>
    </tr>
    <tr>
      <th colspan="2" style="font-size:9px;color:#0052cc">UKI</th>
      <th colspan="2" style="font-size:9px;color:#0052cc">Canada</th>
      <th colspan="2" style="font-size:9px;color:#0052cc">Rest of World</th>
      <th colspan="2" style="font-size:9px;color:#0052cc">Canada</th>
    </tr>
    <tr><th>CBM</th><th>FBP</th><th>Billing Team</th><th>FBP</th><th>CBM</th><th>FBP</th><th>CBM</th><th>FBP</th></tr>
    </thead>
    <tbody id="tableBody"></tbody>
    </table>
    </div>
  </div>
</div>

<!-- AUDIT LOG PANEL -->
<div class="panel" id="panel-log">
  <div class="log-panel">
    <div class="log-header">
      <div class="log-title">&#128203; Audit Log</div>
      <div class="log-controls">
        <input class="log-search" id="logSearch" placeholder="Search logs..." oninput="renderLog()">
        <button class="btn-csv" onclick="exportCSV()">&#8595; Export CSV</button>
        <button class="btn-clear" onclick="clearLog()">Clear log</button>
      </div>
    </div>
    <div class="stats-bar" id="statsBar"></div>
    <div id="logContent"></div>
  </div>
</div>

<!-- CELL POPUP -->
<div class="popup" id="cellPopup">
  <div class="popup-head">Edit cell <button onclick="closePopup()">×</button></div>
  <div class="popup-body">
    <div class="icon-grid" id="iconGrid"></div>
    <label class="off-row"><input type="checkbox" id="chkOff"> Mark as inactive (dimmed)</label>
  </div>
  <div class="popup-footer">
    <button class="btn-cancel2" onclick="closePopup()">Cancel</button>
    <button class="btn-apply" onclick="applyCell()">Apply</button>
  </div>
</div>

<!-- SAVE / LOGIN MODAL -->
<div class="modal-bg" id="saveModal">
  <div class="modal">
    <div class="modal-head">Confirm &amp; save changes <button onclick="closeSaveModal()">×</button></div>
    <div class="modal-body">
      <div class="success-banner" id="successBanner">✓ Changes saved &amp; logged successfully!</div>
      <div id="loginSection">
        <div class="info-box">Sign in to confirm and save. Your username will be recorded in the audit log alongside every change you made.</div>
        <div class="login-err" id="loginErr">Invalid username or password.</div>
        <label>Username</label>
        <input type="text" id="uname" placeholder="e.g. cbm.uki" autocomplete="off">
        <label>Password</label>
        <input type="password" id="pwd" placeholder="••••••••">
        <div class="users-hint">
          <b>Demo accounts</b><br>
          cbm.uki / cbm.canada / cbm.row &nbsp;<span class="rpill p-cbm">CBM</span> — pass123<br>
          fbp.uki / fbp.canada / fbp.row &nbsp;<span class="rpill p-fbp">FBP</span> — pass123<br>
          admin &nbsp;<span class="rpill p-adm">Admin</span> — admin123
        </div>
      </div>
    </div>
    <div class="modal-footer" id="modalFooter">
      <button class="btn-discard" onclick="discardChanges()">Discard changes</button>
      <button class="btn-confirm" onclick="doSaveLogin()">Sign in &amp; save</button>
    </div>
  </div>
</div>

<script>
// ── CONFIG ────────────────────────────────────────────────────────────────────
// Replace with your Google Apps Script Web App URL after deploying
var APPS_SCRIPT_URL = 'YOUR_APPS_SCRIPT_URL_HERE';

// ── USERS ────────────────────────────────────────────────────────────────────
var USERS={
  'cbm.uki':   {pass:'pass123',label:'CBM – UKI'},
  'cbm.canada':{pass:'pass123',label:'CBM – Canada'},
  'cbm.row':   {pass:'pass123',label:'CBM – RoW'},
  'fbp.uki':   {pass:'pass123',label:'FBP – UKI'},
  'fbp.canada':{pass:'pass123',label:'FBP – Canada'},
  'fbp.row':   {pass:'pass123',label:'FBP – RoW'},
  'admin':     {pass:'admin123',label:'Admin'}
};

// ── ICONS ─────────────────────────────────────────────────────────────────────
var ICONS=[
  {val:'R',  cls:'r',  label:'Responsible'},
  {val:'A',  cls:'a',  label:'Accountable'},
  {val:'C',  cls:'c',  label:'Consulted'},
  {val:'I',  cls:'i',  label:'Informed'},
  {val:'R/A',cls:'ra', label:'Resp. & Accountable'},
  {val:'—',  cls:'',   label:'None'},
];

// ── COL LABELS ────────────────────────────────────────────────────────────────
var COL_LABELS=[
  'Keyforce–NetSuite / CBM (UKI)',
  'Keyforce–NetSuite / FBP (UKI)',
  'Rapid–QuickBooks / Billing Team (Canada)',
  'Rapid–QuickBooks / FBP (Canada)',
  'CSS–Navision / CBM (RoW)',
  'CSS–Navision / FBP (RoW)',
  'Serti–Billing / CBM (Canada)',
  'Serti–Billing / FBP (Canada)',
];

// ── DATA ──────────────────────────────────────────────────────────────────────
var SECTIONS=[
  {title:'1. Catalogue & product management',rows:[
    ['New product / SKU setup & activation in source system','all','R','A','R','A','R','A','R','A'],
    ['Pricing maintenance & rate card update','all','C','R/A','R','A','C','R/A','C','R/A'],
    ['Item sync: Salesforce → Boomi → NetSuite','kf','R','I','—','—','—','—','—','—'],
  ]},
  {title:'2. Customer master data management',rows:[
    ['New customer creation (credit check, VAT, mandatory fields)','all','R','A','R','A','R','A','R','A'],
    ['Customer master data amendments (address, billing entity)','all','R/A','I','R/A','I','R/A','I','R/A','I'],
    ['Customer sync: Salesforce → Boomi → NetSuite','kf','R','I','—','—','—','—','—','—'],
  ]},
  {title:'3. Quote to order',rows:[
    ['Quote validation & discount approval','all','R','A','R','A','R','A','R','A'],
    ['Quote conversion to order in CRM / source system','all','R/A','C','R/A','C','R/A','C','R/A','C'],
    ['Order activation & subscription creation in NetSuite ZAB','kf','R','I','—','—','—','—','—','—'],
    ['Billing case creation & pick-up in Salesforce','rq','—','—','R/A','I','—','—','—','—'],
  ]},
  {title:'4. Order to fulfilment & backlog management',rows:[
    ['Backlog recurring review & challenge','all','R','A','R','A','R','A','R','A'],
    ['Order amendments (quantity, site change, deletion)','all','R','A','R','A','R','A','R','A'],
    ['Volume report extraction & population into billing spreadsheet','rq','—','—','R/A','I','—','—','—','—'],
  ]},
  {title:'5. Invoice & billing generation',rows:[
    ['SaaS / HaaS recurring invoice run (NetSuite ZAB)','kf','R/A','I','—','—','—','—','—','—'],
    ['Memorise & generate recurring invoices in QuickBooks','rq','—','—','R/A','I','—','—','—','—'],
    ['Recurring invoice generation in Navision','css','—','—','—','—','R/A','I','—','—'],
    ['Recurring invoice generation in Serti billing module','se','—','—','—','—','—','—','R/A','I'],
    ['One-time & PS invoice generation','all','R','A','R','A','R','A','R','A'],
    ['Invoice delivery & recipient management','all','R/A','I','R/A','I','R/A','I','R/A','I'],
    ['Pro forma invoice generation','all','R','A','R','A','R','A','R','A'],
  ]},
  {title:'6. Credit memos & billing corrections',rows:[
    ['Credit memo request & initiation','all','R','A','R','A','R','A','R','A'],
    ['Credit memo approval (tiered by value & reason)','all','C','A','C','A','C','A','C','A'],
    ['Invoice correction & rebilling','all','R','A','R','A','R','A','R','A'],
  ]},
  {title:'7. Revenue recognition',rows:[
    ['Revenue plan creation & release (IFRS + local GAAP)','kf','I','R/A','—','—','—','—','—','—'],
    ['Revenue release & reconciliation in Navision','css','—','—','—','—','I','R/A','—','—'],
    ['Revenue reconciliation & period-end close','all','C','R/A','C','R/A','C','R/A','C','R/A'],
    ['Contract cost capitalisation & amortisation','all','I','R/A','I','R/A','I','R/A','I','R/A'],
  ]},
  {title:'8. Accounts receivable & cash application',rows:[
    ['Payment receipt & application','all','R','A','R','A','R','A','R','A'],
    ['Dunning & collections escalation','all','R','A','R','A','R','A','R','A'],
    ['Dispute management (contract-related)','all','R','C','R','C','R','C','R','C'],
    ['Bad debt provision review & write-off approval','all','C','R/A','C','R/A','C','R/A','C','R/A'],
    ['Customer reimbursement / refund approval','all','C','A','C','A','C','A','C','A'],
  ]},
  {title:'9. Service contract & subscription management',rows:[
    ['Service contract creation, amendment & maintenance','all','R/A','I','R/A','I','R/A','I','R/A','I'],
    ['Contract termination / early cancellation approval','all','R','A','R','A','R','A','R','A'],
    ['Retail price increase – calculation, comms & ERP update','all','R','A','R','A','R','A','R','A'],
  ]},
  {title:'10. Reporting & governance',rows:[
    ['AR ageing, DSO & collections reporting','all','R','A','R','A','R','A','R','A'],
    ['Win/loss & conversion loss reporting','all','R','A','R','A','R','A','R','A'],
    ['SOX compliance & audit support','all','C','R/A','C','R/A','C','R/A','C','R/A'],
  ]},
];

// ── STATE ─────────────────────────────────────────────────────────────────────
var state=[];
var pendingEdits=[]; // {ri,ci,oldVal,oldOff,newVal,newOff,stepLabel}
var auditLog=[];     // committed log entries
var hasChanges=false;

function buildState(){
  state=[];var ri=0;
  SECTIONS.forEach(function(sec){
    sec.rows.forEach(function(row){
      state[ri]=[];
      for(var ci=0;ci<8;ci++) state[ri][ci]={val:row[ci+2],off:false};
      ri++;
    });
  });
}

function markChanged(){
  hasChanges=true;
  document.getElementById('changesDot').style.display='block';
  document.getElementById('btnSave').disabled=false;
}

// ── TABS ──────────────────────────────────────────────────────────────────────
function switchTab(t){
  ['raci','log'].forEach(function(id){
    document.getElementById('tab-'+id).classList.toggle('active',id===t);
    document.getElementById('panel-'+id).classList.toggle('active',id===t);
  });
  document.getElementById('raciToolbar').style.display=t==='raci'?'flex':'none';
  if(t==='log') renderLog();
}

// ── TABLE BUILD ───────────────────────────────────────────────────────────────
function getStepLabel(ri){
  var idx=0,lbl='';
  SECTIONS.forEach(function(sec){sec.rows.forEach(function(r){if(idx===ri)lbl=r[0];idx++;});});
  return lbl;
}

function buildTable(){
  var tb=document.getElementById('tableBody');tb.innerHTML='';var ri=0;
  SECTIONS.forEach(function(sec){
    var sr=document.createElement('tr');sr.className='section-row';sr.dataset.sec='1';
    sr.innerHTML='<td colspan="9">'+sec.title+'</td>';tb.appendChild(sr);
    sec.rows.forEach(function(row){
      var tr=document.createElement('tr');tr.dataset.sys=row[1];
      var html='<td class="step">'+row[0]+'</td>';
      for(var ci=0;ci<8;ci++) html+='<td id="c_'+ri+'_'+ci+'">'+cellHtml(ri,ci)+'</td>';
      tr.innerHTML=html;tb.appendChild(tr);ri++;
    });
  });
}

function cellHtml(ri,ci){
  var s=state[ri][ci];
  if(s.val==='—') return '<span class="empty" data-cell onclick="openCell('+ri+','+ci+',this)" title="Click to assign">—</span>';
  var cls=s.val==='R/A'?'ra':s.val.toLowerCase();
  return '<span class="badge '+cls+(s.off?' off':'')+'" data-cell onclick="openCell('+ri+','+ci+',this)" title="Click to edit">'+s.val+'</span>';
}

function refreshCell(ri,ci){
  var el=document.getElementById('c_'+ri+'_'+ci);
  if(el) el.innerHTML=cellHtml(ri,ci);
}

// ── FILTER ────────────────────────────────────────────────────────────────────
function filterTable(){
  var v=document.getElementById('sysFilter').value;
  document.querySelectorAll('#tableBody tr:not([data-sec])').forEach(function(r){
    r.style.display=(v==='all'||r.dataset.sys===v||r.dataset.sys==='all')?'':'none';
  });
  document.querySelectorAll('#tableBody tr[data-sec]').forEach(function(s){
    var next=s.nextElementSibling,vis=false;
    while(next&&!next.dataset.sec){if(next.style.display!=='none')vis=true;next=next.nextElementSibling;}
    s.style.display=vis?'':'none';
  });
}

// ── CELL POPUP ────────────────────────────────────────────────────────────────
var editRi=-1,editCi=-1,editSelVal='',editOff=false,popupOpen=false;

function openCell(ri,ci,anchor){
  editRi=ri;editCi=ci;
  var s=state[ri][ci];editSelVal=s.val;editOff=s.off;
  var grid=document.getElementById('iconGrid');grid.innerHTML='';
  ICONS.forEach(function(ic){
    var d=document.createElement('div');
    d.className='icon-opt'+(ic.val===editSelVal?' selected':'');
    d.title=ic.label;
    d.onclick=function(){document.querySelectorAll('.icon-opt').forEach(function(x){x.classList.remove('selected');});d.classList.add('selected');editSelVal=ic.val;};
    d.innerHTML=ic.val==='—'
      ?'<span style="font-size:18px;color:#bbb;line-height:1.4">—</span><span class="lbl">None</span>'
      :'<span class="badge '+ic.cls+'" style="cursor:default;width:32px;height:32px;font-size:12px">'+ic.val+'</span><span class="lbl">'+ic.val+'</span>';
    grid.appendChild(d);
  });
  document.getElementById('chkOff').checked=editOff;
  var popup=document.getElementById('cellPopup');popup.classList.add('open');
  var rect=anchor.getBoundingClientRect();
  var left=rect.left+window.scrollX,top=rect.bottom+window.scrollY+6,pw=260,ph=290;
  if(left+pw>window.innerWidth-10) left=window.innerWidth-pw-10;
  if(top+ph>window.scrollY+window.innerHeight-10) top=rect.top+window.scrollY-ph-6;
  popup.style.left=Math.max(6,left)+'px';popup.style.top=Math.max(6,top)+'px';
  popupOpen=true;
}

function closePopup(){document.getElementById('cellPopup').classList.remove('open');popupOpen=false;editRi=-1;editCi=-1;}

function applyCell(){
  if(editRi<0) return;
  var s=state[editRi][editCi];
  var newOff=document.getElementById('chkOff').checked;
  var changed=(s.val!==editSelVal)||(s.off!==newOff);
  if(changed){
    pendingEdits.push({ri:editRi,ci:editCi,stepLabel:getStepLabel(editRi),col:COL_LABELS[editCi],oldVal:s.val,oldOff:s.off,newVal:editSelVal,newOff:newOff});
    state[editRi][editCi]={val:editSelVal,off:newOff};
    refreshCell(editRi,editCi);
    markChanged();
  }
  closePopup();
}

document.addEventListener('click',function(e){
  if(!popupOpen) return;
  if(!document.getElementById('cellPopup').contains(e.target)&&!e.target.closest('[data-cell]')) closePopup();
});

// ── SAVE MODAL ────────────────────────────────────────────────────────────────
function openSaveModal(){
  document.getElementById('loginErr').style.display='none';
  document.getElementById('successBanner').style.display='none';
  document.getElementById('loginSection').style.display='block';
  document.getElementById('modalFooter').style.display='flex';
  document.getElementById('uname').value='';document.getElementById('pwd').value='';
  document.getElementById('saveModal').classList.add('open');
}
function closeSaveModal(){document.getElementById('saveModal').classList.remove('open');}

function doSaveLogin(){
  var u=document.getElementById('uname').value.trim().toLowerCase();
  var p=document.getElementById('pwd').value;
  if(USERS[u]&&USERS[u].pass===p){
    document.getElementById('loginErr').style.display='none';
    var now=new Date();
    var ts=now.toLocaleString('en-GB',{day:'2-digit',month:'short',year:'numeric',hour:'2-digit',minute:'2-digit',second:'2-digit'});
    var newEntries=pendingEdits.map(function(e){
      return {ts:ts,user:u,userLabel:USERS[u].label,stepLabel:e.stepLabel,col:e.col,oldVal:e.oldVal,oldOff:e.oldOff,newVal:e.newVal,newOff:e.newOff};
    });
    newEntries.forEach(function(entry){auditLog.unshift(entry);});
    pendingEdits=[];
    hasChanges=false;
    document.getElementById('changesDot').style.display='none';
    document.getElementById('btnSave').disabled=true;
    updateLogCount();
    document.getElementById('loginSection').style.display='none';
    document.getElementById('modalFooter').style.display='none';
    document.getElementById('successBanner').style.display='block';
    // Send to Google Sheets if URL is configured
    if(APPS_SCRIPT_URL&&APPS_SCRIPT_URL!=='YOUR_APPS_SCRIPT_URL_HERE'){
      fetch(APPS_SCRIPT_URL,{method:'POST',body:JSON.stringify({entries:newEntries})})
        .catch(function(err){console.warn('Audit log sync failed:',err);});
    }
    // Load latest log from Sheets
    loadAuditLogFromSheets();
    setTimeout(closeSaveModal,2000);
  } else {
    document.getElementById('loginErr').style.display='block';
  }
}

function discardChanges(){
  // revert state
  pendingEdits.forEach(function(e){state[e.ri][e.ci]={val:e.oldVal,off:e.oldOff};refreshCell(e.ri,e.ci);});
  pendingEdits=[];hasChanges=false;
  document.getElementById('changesDot').style.display='none';
  document.getElementById('btnSave').disabled=true;
  closeSaveModal();
}

document.getElementById('pwd').addEventListener('keydown',function(e){if(e.key==='Enter')doSaveLogin();});
document.getElementById('uname').addEventListener('keydown',function(e){if(e.key==='Enter')doSaveLogin();});

// ── AUDIT LOG ─────────────────────────────────────────────────────────────────
function updateLogCount(){
  var cnt=document.getElementById('logCount');
  cnt.textContent=auditLog.length;
  cnt.style.display=auditLog.length?'inline-block':'none';
}

function renderLog(){
  var q=(document.getElementById('logSearch').value||'').toLowerCase();
  var filtered=auditLog.filter(function(e){
    return !q||(e.user+e.stepLabel+e.col+e.ts+e.newVal+e.oldVal).toLowerCase().includes(q);
  });

  // stats
  var users={};
  auditLog.forEach(function(e){users[e.user]=(users[e.user]||0)+1;});
  var topUser=Object.keys(users).sort(function(a,b){return users[b]-users[a];})[0]||'—';
  document.getElementById('statsBar').innerHTML=
    stat(auditLog.length,'Total changes')+
    stat(Object.keys(users).length,'Contributors')+
    stat(topUser,'Most active user');

  var el=document.getElementById('logContent');
  if(!filtered.length){
    el.innerHTML='<div class="log-empty">'+(auditLog.length?'No entries match your search.':'No changes have been saved yet.<br>Make edits to the RACI table and save them to see the log here.')+'</div>';
    return;
  }
  var rows=filtered.map(function(e,idx){
    var oldDisp=e.oldVal+(e.oldOff?' <span class="inactive-tag">inactive</span>':'');
    var newDisp=e.newVal+(e.newOff?' <span class="inactive-tag">inactive</span>':'');
    return '<tr>'
      +'<td class="ts">'+e.ts+'</td>'
      +'<td><strong>'+e.user+'</strong><br><span style="font-size:10px;color:#6b778c">'+e.userLabel+'</span></td>'
      +'<td>'+e.stepLabel+'</td>'
      +'<td style="font-size:11px">'+e.col+'</td>'
      +'<td><span class="val-old">'+oldDisp+'</span><span class="arrow">→</span><span class="val-new">'+newDisp+'</span></td>'
      +'</tr>';
  }).join('');
  el.innerHTML='<table class="log-table"><thead><tr><th>Timestamp</th><th>User</th><th>Process step</th><th>Column</th><th>Change</th></tr></thead><tbody>'+rows+'</tbody></table>';
}

function stat(val,lbl){return '<div class="stat"><div class="stat-n">'+val+'</div><div class="stat-l">'+lbl+'</div></div>';}

function exportCSV(){
  if(!auditLog.length){alert('No audit log entries to export yet.');return;}
  var rows=[['Timestamp','User','User Label','Process Step','Column','Old Value','Old Active','New Value','New Active']];
  auditLog.forEach(function(e){
    rows.push([e.ts,e.user,e.userLabel,e.stepLabel,e.col,e.oldVal,e.oldOff?'No':'Yes',e.newVal,e.newOff?'No':'Yes']);
  });
  var csv=rows.map(function(r){return r.map(function(c){return '"'+String(c).replace(/"/g,'""')+'"';}).join(',');}).join('\n');
  var a=document.createElement('a');
  a.href='data:text/csv;charset=utf-8,'+encodeURIComponent(csv);
  a.download='RACI_Audit_Log_'+new Date().toISOString().slice(0,10)+'.csv';
  a.click();
}

function clearLog(){
  if(!auditLog.length) return;
  if(!confirm('Clear the entire audit log? This cannot be undone.')) return;
  auditLog=[];updateLogCount();renderLog();
}

// ── GOOGLE SHEETS SYNC ───────────────────────────────────────────────────────
function loadAuditLogFromSheets(){
  if(!APPS_SCRIPT_URL||APPS_SCRIPT_URL==='YOUR_APPS_SCRIPT_URL_HERE') return;
  fetch(APPS_SCRIPT_URL)
    .then(function(r){return r.json();})
    .then(function(data){
      if(data.status==='ok'&&data.entries.length){
        auditLog=data.entries.reverse().map(function(e){
          return {
            ts:e['Timestamp'],user:e['User'],userLabel:e['User Label'],
            stepLabel:e['Process Step'],col:e['Column'],
            oldVal:e['Old Value'],oldOff:e['Old Active']==='Inactive',
            newVal:e['New Value'],newOff:e['New Active']==='Inactive'
          };
        });
        updateLogCount();
        if(document.getElementById('panel-log').classList.contains('active')) renderLog();
      }
    })
    .catch(function(err){console.warn('Could not load audit log from Sheets:',err);});
}

// ── INIT ──────────────────────────────────────────────────────────────────────
buildState();buildTable();filterTable();loadAuditLogFromSheets();
</script>
</body>
</html>
