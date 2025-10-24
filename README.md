<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>FUPRE Expert Opinion Questionnaire</title>
<style>
  :root{
    --ink:#0b1b40; --muted:#5a6473; --accent:#0b57d0; --danger:#b3261e; --bg:#f6f8fb;
    --card:#ffffff; --line:#e7eef7;
  }
  *{box-sizing:border-box}
  body{margin:0;font-family:system-ui,Arial,sans-serif;background:var(--bg);color:#111;}
  .wrap{max-width:960px;margin:0 auto;padding:16px;}
  .card{background:var(--card);border-radius:14px;box-shadow:0 8px 28px rgba(0,0,0,.08);padding:18px 18px 24px;}

  header h1{margin:0;color:var(--ink);font-weight:800;font-size:1rem;text-transform:uppercase;}
  header h2{margin:.15rem 0 .75rem;color:var(--ink);font-size:1.2rem;font-weight:800;}
  p.muted{color:var(--muted);margin:.25rem 0 1rem;}
  hr{border:0;border-top:1px solid var(--line);margin:12px 0 18px;}

  .progress-wrap{position:sticky;top:0;background:#fff;z-index:10;margin:-18px -18px 12px -18px;padding:12px 18px;border-radius:14px 14px 0 0;border-bottom:1px solid var(--line)}
  .progress-label{display:flex;justify-content:space-between;align-items:center;font-size:.9rem;color:var(--muted);margin-bottom:6px}
  .bar{height:8px;background:#e9edf7;border-radius:999px;overflow:hidden}
  .bar > i{display:block;height:100%;width:0;background:linear-gradient(90deg,#3b82f6,#0b57d0);border-radius:999px;transition:width .35s ease-in-out}

  label{display:block;margin:16px 0 6px;font-weight:600;}
  input[type=text], select{width:100%;padding:10px;border:1px solid #dcdcdc;border-radius:10px;background:#fff;font-size:1rem}
  .help{font-size:.9rem;color:var(--muted)}
  .note{background:#f7fafb;border:1px solid #e1e8f2;border-radius:10px;padding:10px 12px;font-size:.95rem;color:#2c3b50;margin-top:8px}

  .nav{display:flex;gap:10px;justify-content:space-between;margin-top:20px}
  .btn{padding:12px 18px;border:0;border-radius:12px;font-weight:700;cursor:pointer}
  .btn-next{background:var(--accent);color:#fff}
  .btn-back{background:var(--danger);color:#fff}

  .panel{display:none;animation:.25s ease-in-out fadeSlide}
  .panel.active{display:block}
  @keyframes fadeSlide{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}

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
      <section class="panel active" data-kind="sectionA">
        <h3>SECTION A — Respondent Information</h3>

        <label>Name (Optional)</label>
        <input type="text" id="name" />

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
          <option value="">Select…</option>
          <option>10–15 years</option><option>15–25 years</option><option>Above 25 years</option>
        </select>

        <label>Operational Sector (Select multiple)</label>
        <select id="sector" multiple>
          <option>Shipyard Maintenance</option><option>Dockyard Maintenance</option><option>Fleet Support Group</option><option>Ports Operations</option><option>Others</option>
        </select>

        <label>If Others, specify:</label>
        <input type="text" id="others"/>

        <div class="nav">
          <button class="btn btn-back" disabled>← Back</button>
          <button class="btn btn-next" id="toAHP">Next →</button>
        </div>
      </section>

      <!-- AHP pages will be inserted here -->

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
/* ENTRY IDs */
const E={name:"entry.1178874589",sex:"entry.998624902",age:"entry.468327871",position:"entry.1969678186",experience:"entry.1750155354",sector:"entry.738891609",others:"entry.1589522648",topsis_cbm:"entry.24218855",topsis_ship:"entry.422667084",topsis_reg:"entry.1926731615",topsis_pms:"entry.1229987298"};

/* AHP LIST (Exact pairs mapped already) */
const AHP=[ /* SAME LIST AS PREVIOUS VERSION — NOT SHORTENED */ 
{entry:"entry.285442853",L:"BS",R:"ST"},
{entry:"entry.1157544231",L:"BS",R:"DA"},
{entry:"entry.559726709",L:"BS",R:"TC"},
{entry:"entry.1145869432",L:"BS",R:"MR"},
{entry:"entry.386731795",L:"BS",R:"PMS"},
{entry:"entry.1636529645",L:"BL",R:"BS"},
{entry:"entry.107098696",L:"BS",R:"CSS"},
{entry:"entry.108322282",L:"ST",R:"DA"},
{entry:"entry.1951403273",L:"TC",R:"ST"},
{entry:"entry.238248158",L:"ST",R:"BP"},
{entry:"entry.1583513457",L:"ST",R:"MR"},
{entry:"entry.1433257728",L:"ST",R:"PMS"},
{entry:"entry.1019478353",L:"ST",R:"BL"},
{entry:"entry.601680915",L:"ST",R:"CSS"},
{entry:"entry.1353298016",L:"TC",R:"DA"},
{entry:"entry.210487843",L:"DA",R:"BP"},
{entry:"entry.734169370",L:"MR",R:"DA"},
{entry:"entry.253871562",L:"PMS",R:"DA"},
{entry:"entry.877177064",L:"DA",R:"BL"},
{entry:"entry.5223062",L:"DA",R:"CSS"},
{entry:"entry.1958369010",L:"TC",R:"MR"},
{entry:"entry.386126691",L:"TC",R:"PMS"},
{entry:"entry.781406704",L:"BL",R:"TC"},
{entry:"entry.1540085231",L:"TC",R:"CSS"},
{entry:"entry.1009434225",L:"BP",R:"MR"},
{entry:"entry.641865933",L:"BP",R:"PMS"},
{entry:"entry.456829582",L:"BL",R:"BP"},
{entry:"entry.1239402805",L:"BP",R:"CSS"},
{entry:"entry.128111684",L:"PMS",R:"MR"},
{entry:"entry.1423346165",L:"BL",R:"MR"},
{entry:"entry.1646882010",L:"MR",R:"CSS"},
{entry:"entry.1180678900",L:"BL",R:"PMS"},
{entry:"entry.1870568078",L:"PMS",R:"CSS"},
{entry:"entry.112208730",L:"BL",R:"CSS"},
];

function ahpOptions(L,R){
return[
`${L} is moderately more important than ${R} (3)`,
`${L} is strongly more important than ${R} (5)`,
`${L} is very strongly more important than ${R} (7)`,
`${L} is extremely more important than ${R} (9)`,
`Both criteria are equally important (1)`,
`${R} is moderately more important than ${L} (3)`,
`${R} is strongly more important than ${L} (5)`,
`${R} is very strongly more important than ${L} (7)`,
`${R} is extremely more important than ${L} (9)`
];
}

function injectAHP(){
const container=document.getElementById("panels");
const beforeTopsis=container.querySelector('[data-kind="topsis"]');
AHP.forEach(pair=>{
const sec=document.createElement("section");
sec.className="panel";
sec.dataset.kind="ahp";
sec.dataset.entry=pair.entry;
sec.innerHTML=`
<h3>SECTION B — Pairwise Comparison (AHP)</h3>
<div class="note">Use the AHP 1–9 scale of importance.</div>
<label>Compare: <b>${pair.L}</b> vs <b>${pair.R}</b></label>
<select class="ahpSel" required>
<option value="">Select…</option>
${ahpOptions(pair.L,pair.R).map(o=>`<option>${o}</option>`).join("")}
</select>
<div class="nav"><button class="btn btn-back">← Back</button><button class="btn btn-next">Next →</button></div>
`;
container.insertBefore(sec,beforeTopsis);
});
}

function collectSectionA(){return{
[E.name]:document.getElementById("name").value.trim(),
[E.sex]:document.getElementById("sex").value.trim(),
[E.age]:document.getElementById("age").value.trim(),
[E.position]:document.getElementById("position").value.trim(),
[E.experience]:document.getElementById("experience").value.trim(),
[E.sector]:Array.from(document.getElementById("sector").selectedOptions).map(o=>o.value).join(", "),
[E.others]:document.getElementById("others").value.trim()
};}

function collectAHP(){
const out={};
document.querySelectorAll('.panel[data-kind="ahp"]').forEach(p=>{
out[p.dataset.entry]=p.querySelector(".ahpSel").value;
});
return out;
}

function collectTopsis(){return{
[E.topsis_cbm]:document.getElementById("topsis_cbm").value.trim(),
[E.topsis_ship]:document.getElementById("topsis_ship").value.trim(),
[E.topsis_reg]:document.getElementById("topsis_reg").value.trim(),
[E.topsis_pms]:document.getElementById("topsis_pms").value.trim()
};}

function validate(i){
const p=PANELS[i];
if(p.dataset.kind==="sectionA") return ["sex","age","position","experience"].every(id=>document.getElementById(id).value);
if(p.dataset.kind==="ahp") return p.querySelector(".ahpSel").value;
if(p.dataset.kind==="topsis") return ["topsis_cbm","topsis_ship","topsis_reg","topsis_pms"].every(id=>document.getElementById(id).value);
return true;
}

function setProgress(){
const step=idx+1,total=PANELS.length,pct=Math.round(step/total*100);
document.getElementById("progPct").textContent=pct+"%";
document.getElementById("progBar").style.width=pct+"%";
document.getElementById("progText").textContent=
PANELS[idx].dataset.kind==="ahp" ? `AHP ${idx} of ${total-2}` :
PANELS[idx].dataset.kind==="topsis" ? `TOPSIS` :
`Section A`;
}

function show(i){
PANELS.forEach(p=>p.classList.remove("active"));
PANELS[i].classList.add("active");
idx=i; setProgress();
}

let PANELS,idx=0;

window.onload=()=>{
injectAHP();
PANELS=[...document.querySelectorAll(".panel")];
setProgress();

PANELS.forEach((p,i)=>{
const next=p.querySelector(".btn-next");
const back=p.querySelector(".btn-back");
if(next) next.onclick=()=>{if(!validate(i)) return alert("Please complete this page."); show(i+1);}
if(back) back.onclick=()=>show(i-1);
});

document.getElementById("submitBtn").onclick=async()=>{
if(!validate(PANELS.length-1)) return alert("Complete all fields.");
const fd=new FormData();[...Object.entries(collectSectionA()),...Object.entries(collectAHP()),...Object.entries(collectTopsis())].forEach(([k,v])=>fd.append(k,v));
await fetch("https://docs.google.com/forms/d/e/1FAIpQLScB5qIHoNCvtbn0UERpQT83ZRWHLXNWSlEgKc3ta4wjKByzdw/formResponse",{method:"POST",body:fd,mode:"no-cors"});
document.querySelector(".progress-wrap").style.display="none";
document.getElementById("panels").style.display="none";
document.getElementById("doneView").style.display="block";
};
};
</script>
</body>
</html>
