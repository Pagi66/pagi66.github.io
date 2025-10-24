<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>FUPRE Expert Opinion Questionnaire</title>
<style>
  :root{
    --ink:#0b1b40; --muted:#5a6473; --accent:#0b57d0; --danger:#b3261e; --bg:#f6f8fb;
    --card:#ffffff; --line:#e7eef7;
  }
  *{box-sizing:border-box}
  body{margin:0;font-family:system-ui,Arial,sans-serif;background:var(--bg);color:#111}
  .wrap{max-width:960px;margin:0 auto;padding:16px}
  .card{background:var(--card);border-radius:14px;box-shadow:0 8px 28px rgba(0,0,0,.08);padding:18px 18px 24px}

  header h1{margin:0;color:var(--ink);font-weight:800;font-size:1rem;text-transform:uppercase}
  header h2{margin:.15rem 0 .75rem;color:var(--ink);font-size:1.2rem;font-weight:800}
  p.muted{color:var(--muted);margin:.25rem 0 1rem}
  hr{border:0;border-top:1px solid var(--line);margin:12px 0 18px}

  .progress-wrap{position:sticky;top:0;background:#fff;z-index:10;margin:-18px -18px 12px -18px;padding:12px 18px;border-radius:14px 14px 0 0;border-bottom:1px solid var(--line)}
  .progress-label{display:flex;justify-content:space-between;align-items:center;font-size:.9rem;color:var(--muted);margin-bottom:6px}
  .bar{height:8px;background:#e9edf7;border-radius:999px;overflow:hidden}
  .bar > i{display:block;height:100%;width:0;background:linear-gradient(90deg,#3b82f6,#0b57d0);border-radius:999px;transition:width .35s ease-in-out}

  label{display:block;margin:16px 0 6px;font-weight:600}
  input[type=text],select{width:100%;padding:10px;border:1px solid #dcdcdc;border-radius:10px;background:#fff;font-size:1rem}
  .help{font-size:.9rem;color:var(--muted)}
  .note{background:#f7fafb;border:1px solid #e1e8f2;border-radius:10px;padding:10px 12px;font-size:.95rem;color:#2c3b50;margin-top:8px}

  .nav{display:flex;gap:10px;justify-content:space-between;margin-top:20px}
  .btn{padding:12px 18px;border:0;border-radius:12px;font-weight:700;cursor:pointer}
  .btn-next{background:var(--accent);color:#fff}
  .btn-back{background:var(--danger);color:#fff}
  .btn[disabled]{opacity:.6;cursor:not-allowed}

  .panel{display:none;animation:.25s ease-in-out fadeSlide}
  .panel.active{display:block}
  @keyframes fadeSlide{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}

  /* Slider UI */
  .pair-head{display:flex;justify-content:space-between;align-items:center;gap:10px;margin-top:10px}
  .pair-left,.pair-right{font-weight:700;color:#0b1b40;max-width:45%}
  .slider-row{display:flex;align-items:center;gap:10px;margin-top:12px}
  input[type=range]{width:100%}
  .ticks{display:flex;justify-content:space-between;font-size:.85rem;color:#5a6473;margin-top:6px}
  .scale-legend{font-size:.9rem;color:#5a6473;margin-top:8px}

  .done{display:none;text-align:left}
  .done h3{margin:0 0 8px}
  .footer{margin-top:22px;padding-top:10px;border-top:1px dashed var(--line);color:var(--muted);font-size:.95rem;white-space:pre-line}
</style>
</head>
<body>
<div class="wrap">
  <div class="card">
    <header>
      <h1>FEDERAL UNIVERSITY OF PETROLEUM RESOURCES, EFFURUN</h1>
      <h1>DEPARTMENT OF MARINE ENGINEERING</h1>
      <h2>EXPERT OPINION FORM ON MARINE MACHINERY MAINTENANCE CRITERIA (NNS)</h2>
    </header>

    <p class="muted">This questionnaire collects expert judgment on criteria influencing maintenance decision-making onboard Nigerian Navy Ships (NNS). All responses are confidential and strictly for academic research.</p>
    <hr/>

    <div class="progress-wrap">
      <div class="progress-label">
        <div id="progText">Section A</div>
        <div id="progPct">0%</div>
      </div>
      <div class="bar"><i id="progBar"></i></div>
    </div>

    <div id="panels">
      <!-- SECTION A -->
      <section class="panel active" data-kind="sectionA">
        <h3>SECTION A — Respondent Information</h3>
        <label>Name (Optional)</label>
        <input type="text" id="name"/>

        <label>Sex</label>
        <select id="sex" required><option value="">Select…</option><option>Male</option><option>Female</option></select>

        <label>Age Range</label>
        <select id="age" required>
          <option value="">Select…</option><option>30–40</option><option>40–50</option><option>50–60</option><option>Above 60 years</option>
        </select>

        <label>Position / Role</label>
        <select id="position" required>
          <option value="">Select…</option>
          <option>Marine Engineering Officer</option>
          <option>Weapon Engineering Officer</option>
          <option>Ship Repair/Maintenance Officer</option>
          <option>Dock Master</option>
          <option>Naval Architect</option>
          <option>Marine Engineering Consultant</option>
        </select>

        <label>Years of Experience</label>
        <select id="experience" required>
          <option value="">Select…</option><option>10–15 years</option><option>15–25 years</option><option>Above 25 years</option>
        </select>

        <label>Operational Sector (Select multiple)</label>
        <select id="sector" multiple>
          <option>Shipyard Maintenance</option><option>Dockyard Maintenance</option><option>Maritime</option><option>Ports Operations</option><option>Fleet Support Group</option><option>Others</option>
        </select>

        <label>If Others, specify</label>
        <input type="text" id="others"/>

        <div class="nav">
          <button class="btn btn-back" disabled>← Back</button>
          <button class="btn btn-next" id="toAHP">Next →</button>
        </div>
      </section>

      <!-- AHP INTRO PANEL -->
      <section class="panel" data-kind="introAHP">
        <h3>SECTION B — Analytical Hierarchy Process (AHP)</h3>
        <div class="note">
          In the next screens you will compare two criteria at a time and judge which one is more important for maintenance decision-making.
        </div>

        <h4 style="margin-top:14px">AHP Judgement Scale (Saaty)</h4>
        <table style="width:100%;font-size:.95rem;border-collapse:collapse">
          <tr><td style="width:40px"><b>1</b></td><td>Both criteria are equally important.</td></tr>
          <tr><td><b>3</b></td><td>One is moderately more important.</td></tr>
          <tr><td><b>5</b></td><td>One is strongly more important.</td></tr>
          <tr><td><b>7</b></td><td>One is very strongly more important.</td></tr>
          <tr><td><b>9</b></td><td>One is extremely more important.</td></tr>
        </table>
        <div class="note" style="margin-top:12px">
          Example: If you believe <b>Berth Services (BS)</b> is strongly more important than <b>Sea Trial (ST)</b>, move the slider towards <b>BS</b> until it reads <b>5</b>.
        </div>

        <div class="nav">
          <button class="btn btn-back">← Back</button>
          <button class="btn btn-next">Proceed to Comparisons →</button>
        </div>
      </section>

      <!-- AHP pages will be injected here -->

      <!-- TOPSIS -->
      <section class="panel" data-kind="topsis">
        <h3>SECTION C — TOPSIS Ratings</h3>

        <label>Condition Based Maintenance (CBM)</label>
        <select id="topsis_cbm" required><option value="">Rate 1–10</option><option>1</option><option>2</option><option>3</option><option>4</option><option>5</option><option>6</option><option>7</option><option>8</option><option>9</option><option>10</option></select>

        <label>Ship Husbandry</label>
        <select id="topsis_ship" required><option value="">Rate 1–10</option><option>1</option><option>2</option><option>3</option><option>4</option><option>5</option><option>6</option><option>7</option><option>8</option><option>9</option><option>10</option></select>

        <label>Regulation of Dock Operations</label>
        <select id="topsis_reg" required><option value="">Rate 1–10</option><option>1</option><option>2</option><option>3</option><option>4</option><option>5</option><option>6</option><option>7</option><option>8</option><option>9</option><option>10</option></select>

        <label>Planned Maintenance Schedule (PMS)</label>
        <select id="topsis_pms" required><option value="">Rate 1–10</option><option>1</option><option>2</option><option>3</option><option>4</option><option>5</option><option>6</option><option>7</option><option>8</option><option>9</option><option>10</option></select>

        <div class="nav">
          <button class="btn btn-back">← Back</button>
          <button class="btn btn-next" id="submitBtn">Submit</button>
        </div>
      </section>

      <!-- THANK YOU -->
      <section class="done" id="doneView">
        <h3>✔ Response Submitted</h3>
        <p class="muted">Thank you for your expert input. Your response supports improved maintenance planning aboard Nigerian Navy Ships.</p>
        <div class="footer">
Research conducted by:
LT A. S. OGBOANOH
Department of Marine Engineering
Federal University of Petroleum Resources, Effurun (FUPRE)
For Academic Research Purposes Only
        </div>
      </section>
    </div>
  </div>
</div>

<script>
/* === ENTRY IDs (confirmed) === */
const E={
  name:"entry.1178874589",
  sex:"entry.998624902",
  age:"entry.468327871",
  position:"entry.1969678186",
  experience:"entry.1750155354",
  sector:"entry.738891609",
  others:"entry.1589522648",
  topsis_cbm:"entry.24218855",
  topsis_ship:"entry.422667084",
  topsis_reg:"entry.1926731615",
  topsis_pms:"entry.1229987298"
};

/* === AHP PAIRS (34) — full labels to generate the exact Google option strings === */
const AHP = [
  { entry:"entry.285442853",  L:"Berth Services (BS)", R:"Sea Trial (ST)" },
  { entry:"entry.1157544231", L:"Berth Services (BS)", R:"Docking Area (DA)" },
  { entry:"entry.559726709",  L:"Berth Services (BS)", R:"Tank Cleansing (TC)" },
  { entry:"entry.1145869432", L:"Berth Services (BS)", R:"Maritime Rules (MR)" },
  { entry:"entry.386731795",  L:"Berth Services (BS)", R:"Planned Maintenance Schedule (PMS)" },
  { entry:"entry.1636529645", L:"Berth Length (BL)",  R:"Berth Services (BS)" },
  { entry:"entry.107098696",  L:"Berth Services (BS)", R:"Compartment and Ship Size (CSS)" },

  { entry:"entry.108322282",  L:"Sea Trial (ST)", R:"Docking Area (DA)" },
  { entry:"entry.1951403273", L:"Tank Cleansing (TC)", R:"Sea Trial (ST)" },
  { entry:"entry.238248158",  L:"Sea Trial (ST)", R:"Blasting and Painting (BP)" },
  { entry:"entry.1583513457", L:"Sea Trial (ST)", R:"Maritime Rules (MR)" },
  { entry:"entry.1433257728", L:"Sea Trial (ST)", R:"Planned Maintenance Schedule (PMS)" },
  { entry:"entry.1019478353", L:"Sea Trial (ST)", R:"Berth Length (BL)" },
  { entry:"entry.601680915",  L:"Sea Trial (ST)", R:"Compartment and Ship Size (CSS)" },

  { entry:"entry.1353298016", L:"Tank Cleansing (TC)", R:"Docking Area (DA)" },
  { entry:"entry.210487843",  L:"Docking Area (DA)", R:"Blasting and Painting (BP)" },
  { entry:"entry.734169370",  L:"Maritime Rules (MR)", R:"Docking Area (DA)" },
  { entry:"entry.253871562",  L:"Planned Maintenance Schedule (PMS)", R:"Docking Area (DA)" },
  { entry:"entry.877177064",  L:"Docking Area (DA)", R:"Berth Length (BL)" },
  { entry:"entry.5223062",    L:"Docking Area (DA)", R:"Compartment and Ship Size (CSS)" },

  { entry:"entry.1958369010", L:"Tank Cleansing (TC)", R:"Maritime Rules (MR)" },
  { entry:"entry.386126691",  L:"Tank Cleansing (TC)", R:"Planned Maintenance Schedule (PMS)" },
  { entry:"entry.781406704",  L:"Berth Length (BL)",  R:"Tank Cleansing (TC)" },
  { entry:"entry.1540085231", L:"Tank Cleansing (TC)", R:"Compartment and Ship Size (CSS)" },

  { entry:"entry.1009434225", L:"Blasting and Painting (BP)", R:"Maritime Rules (MR)" },
  { entry:"entry.641865933",  L:"Blasting and Painting (BP)", R:"Planned Maintenance Schedule (PMS)" },
  { entry:"entry.456829582",  L:"Berth Length (BL)",  R:"Blasting and Painting (BP)" },
  { entry:"entry.1239402805", L:"Blasting and Painting (BP)", R:"Compartment and Ship Size (CSS)" },

  { entry:"entry.128111684",  L:"Planned Maintenance Schedule (PMS)", R:"Maritime Rules (MR)" },
  { entry:"entry.1423346165", L:"Berth Length (BL)",  R:"Maritime Rules (MR)" },
  { entry:"entry.1646882010", L:"Maritime Rules (MR)", R:"Compartment and Ship Size (CSS)" },
  { entry:"entry.1180678900", L:"Berth Length (BL)",  R:"Planned Maintenance Schedule (PMS)" },
  { entry:"entry.1870568078", L:"Planned Maintenance Schedule (PMS)", R:"Compartment and Ship Size (CSS)" },
  { entry:"entry.112208730",  L:"Berth Length (BL)",  R:"Compartment and Ship Size (CSS)" }
];

/* === Slider (pure Saaty): allowed positions [-9,-7,-5,-3,0,3,5,7,9] === */
const SAATY_VALUES = [-9,-7,-5,-3,0,3,5,7,9];
const LABEL_FOR = (abs) => ({
  0: "Both criteria are equally important (1)",
  3: "(3) — Moderately",
  5: "(5) — Strongly",
  7: "(7) — Very strongly",
  9: "(9) — Extremely"
})[abs] || "";

/* ==== Wizard State ==== */
let PANELS=[], idx=0;

/* Build an option sentence EXACTLY like Google Form expects */
function sentenceFrom(L, R, v){
  if (v===0) return "Both criteria are equally important (1)";
  const abs = Math.abs(v);
  const scaleWord = {3:"moderately",5:"strongly",7:"very strongly",9:"extremely"}[abs] || "";
  if (v>0) return `${L} is ${scaleWord} more important than ${R} (${abs})`;
  return `${R} is ${scaleWord} more important than ${L} (${abs})`;
}

/* Inject AHP pages (slider UI) */
function injectAHP(){
  const container=document.getElementById("panels");
  const beforeTopsis=container.querySelector('[data-kind="topsis"]');

  AHP.forEach((item,i)=>{
    const sec=document.createElement("section");
    sec.className="panel";
    sec.dataset.kind="ahp";
    sec.dataset.entry=item.entry;
    sec.dataset.index=i+1;

    sec.innerHTML = `
      <h3>SECTION B — Pairwise Comparison (AHP)</h3>
      <div class="note">Move the slider toward the criterion you judge more important.</div>

      <div class="pair-head">
        <div class="pair-left">${item.L}</div>
        <div class="pair-right" style="text-align:right">${item.R}</div>
      </div>

      <div class="slider-row">
        <span style="min-width:24px;text-align:center">←</span>
        <input type="range" min="-9" max="9" step="1" value="0" class="ahpRange"/>
        <span style="min-width:24px;text-align:center">→</span>
      </div>

      <div class="ticks">
        <span>-9</span><span>-7</span><span>-5</span><span>-3</span><span>0</span><span>3</span><span>5</span><span>7</span><span>9</span>
      </div>

      <div class="scale-legend" data-legend>Importance: 1 — Both criteria are equally important</div>

      <div class="nav">
        <button class="btn btn-back">← Back</button>
        <button class="btn btn-next">Next →</button>
      </div>
    `;
    container.insertBefore(sec,beforeTopsis);

    // snap to allowed values + live label
    const range = sec.querySelector(".ahpRange");
    const legend = sec.querySelector("[data-legend]");
    const updateLegend = ()=>{
      // snap
      let v=parseInt(range.value,10);
      // find nearest allowed
      let nearest = SAATY_VALUES.reduce((p,c)=>Math.abs(c-v)<Math.abs(p-v)?c:p, SAATY_VALUES[0]);
      range.value = nearest;
      const abs = Math.abs(nearest);
      legend.textContent = (nearest===0)
        ? "Importance: 1 — Both criteria are equally important"
        : `Importance: ${abs} ${LABEL_FOR(abs).split("—")[1]} (${nearest>0?item.L+' > '+item.R:item.R+' > '+item.L})`;
    };
    range.addEventListener("input", updateLegend, {passive:true});
    range.addEventListener("change", updateLegend);
    updateLegend();
  });
}

/* Collectors */
function collectSectionA(){
  return {
    [E.name]: document.getElementById("name").value.trim(),
    [E.sex]: document.getElementById("sex").value.trim(),
    [E.age]: document.getElementById("age").value.trim(),
    [E.position]: document.getElementById("position").value.trim(),
    [E.experience]: document.getElementById("experience").value.trim(),
    // For checkbox-style fields, append each selected option separately (Google accepts repeated keys)
    _sectorMulti: Array.from(document.getElementById("sector").selectedOptions).map(o=>o.value),
    [E.others]: document.getElementById("others").value.trim()
  };
}
function collectAHP(){
  const out={};
  document.querySelectorAll('.panel[data-kind="ahp"]').forEach(p=>{
    const entry = p.dataset.entry;
    const L = AHP.find(x=>x.entry===entry).L;
    const R = AHP.find(x=>x.entry===entry).R;
    const v = parseInt(p.querySelector(".ahpRange").value,10);
    out[entry] = sentenceFrom(L,R,v);
  });
  return out;
}
function collectTopsis(){return{
  [E.topsis_cbm]: document.getElementById("topsis_cbm").value.trim(),
  [E.topsis_ship]: document.getElementById("topsis_ship").value.trim(),
  [E.topsis_reg]: document.getElementById("topsis_reg").value.trim(),
  [E.topsis_pms]: document.getElementById("topsis_pms").value.trim()
};}

/* Validation */
function validate(i){
  const p = PANELS[i];
  if (p.dataset.kind==="sectionA"){
    return ["sex","age","position","experience"].every(id=>document.getElementById(id).value);
  }
  if (p.dataset.kind==="ahp"){ return true; } // slider always has a value (defaults to 0 = equal)
  if (p.dataset.kind==="topsis"){
    return ["topsis_cbm","topsis_ship","topsis_reg","topsis_pms"].every(id=>document.getElementById(id).value);
  }
  return true;
}

/* Progress */
function setProgress(){
  const step = idx+1, total = PANELS.length;
  const pct = Math.round(step/total*100);
  document.getElementById("progPct").textContent = pct+"%";
  document.getElementById("progBar").style.width = pct+"%";
  const kind = PANELS[idx].dataset.kind;
  document.getElementById("progText").textContent =
    kind==="introAHP" ? "AHP — Instructions" :
    kind==="ahp"     ? `AHP ${PANELS[idx].dataset.index} of ${AHP.length}` :
    kind==="topsis"  ? "TOPSIS" : "Section A";
}
function show(i){
  PANELS.forEach(p=>p.classList.remove("active"));
  PANELS[i].classList.add("active");
  idx=i; setProgress();
}

/* Init */
window.addEventListener("load", ()=>{
  injectAHP();
  PANELS = [...document.querySelectorAll(".panel")];
  setProgress();

  // Bind nav for all panels
  PANELS.forEach((p,i)=>{
    const next = p.querySelector(".btn-next");
    const back = p.querySelector(".btn-back");
    if (next) next.addEventListener("click", ()=>{
      if (!validate(i)) { alert("Please complete this page to proceed."); return; }
      show(Math.min(i+1, PANELS.length-1));
    });
    if (back) back.addEventListener("click", ()=> show(Math.max(i-1,0)));
  });

  // Submit — fetch to Google, then show internal thank-you
  document.getElementById("submitBtn").addEventListener("click", async ()=>{
    if (!validate(PANELS.length-1)) { alert("Please complete this page."); return; }

    // Build FormData (append multi-select sector as repeated keys)
    const fd = new FormData();
    const A = collectSectionA(), B = collectAHP(), C = collectTopsis();
    Object.entries(A).forEach(([k,v])=>{
      if (k==="_sectorMulti"){
        v.forEach(val=>fd.append(E.sector, val));
      } else {
        fd.append(k,v);
      }
    });
    Object.entries(B).forEach(([k,v])=>fd.append(k,v));
    Object.entries(C).forEach(([k,v])=>fd.append(k,v));

    await fetch(
      "https://docs.google.com/forms/d/e/1FAIpQLScB5qIHoNCvtbn0UERpQT83ZRWHLXNWSlEgKc3ta4wjKByzdw/formResponse",
      { method:"POST", body:fd, mode:"no-cors" }
    );

    // Internal thank-you
    document.querySelector(".progress-wrap").style.display="none";
    document.getElementById("panels").style.display="none";
    document.getElementById("doneView").style.display="block";
  });
});
</script>
</body>
</html>
