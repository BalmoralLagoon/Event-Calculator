# Event-Calculator
<!-- ===== Balmoral Lagoon – Interactive Pricing Calculator ===== -->
<link rel="preconnect" href="https://fonts.gstatic.com">
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&display=swap" rel="stylesheet">
<style>
  :root{--navy:#0F4876;--deep:#163963;--gold:#CB9700;--bg:#F7F9FC;}
  body{font-family:'Montserrat',sans-serif;background:var(--bg);color:var(--deep);}
  .wrap{max-width:520px;margin:0 auto;padding:24px;border-radius:18px;background:#fff;
        box-shadow:0 6px 14px rgba(0,0,0,.1);}
  h2{margin:0 0 12px;font-size:1.6rem;color:var(--navy);}
  label{font-weight:600;margin-top:18px;display:block;}
  select,input{width:100%;padding:10px 12px;border:2px solid var(--navy);border-radius:10px;font-size:1rem;}
  input::-webkit-inner-spin-button,input::-webkit-outer-spin-button{display:none;}
  .total{margin:26px 0 12px;font-size:1.6rem;font-weight:700;text-align:center;
         border-top:2px dashed var(--gold);padding-top:18px;}
  .cta{display:block;text-align:center;background:var(--gold);color:#fff;padding:14px 0;margin-top:8px;
       border-radius:50px;font-weight:700;text-decoration:none;}
</style>

<div class="wrap">
  <h2>Plan Your Perfect Lagoon Event 🌊</h2>

  <label>Venue</label>
  <select id="venue">
    <option selected disabled>— choose —</option>
    <option>Serenity Beach Pavilion</option>
    <option>Paradise Palms Pavilion</option>
    <option>Celebration Lawn</option>
    <option>Small Pavilion</option>
    <option>Splash Pad Pavilion</option>
    <option>Meeting Room</option>
    <option>Meeting Room + Patio</option>
    <option>Castle Hall</option>
  </select>

  <label>Package / Time</label>
  <select id="time">
    <option selected disabled>— choose —</option>
    <option value="3hr">3 hours</option>
    <option value="7hr">7 hours</option>
    <option value="early">Early&nbsp;(11 AM–6 PM)</option>
    <option value="late">Late&nbsp;(3 PM–11 PM)</option>
    <option value="fullday">Full Day (Castle Hall only)</option>
  </select>

  <label>Extra member guests ($10 ea)</label>
  <input id="mem" type="number" min="0" value="0">

  <label>Extra non‑member guests ($20 ea)</label>
  <input id="non" type="number" min="0" value="0">

  <label>Extra event hours ($200 / hr)</label>
  <input id="hrs" type="number" min="0" value="0">

  <div class="total" id="total">$0.00</div>
  <a href="mailto:events@lagoonfanatics.com?subject=Event%20Inquiry" class="cta">Submit Inquiry</a>
</div>

<script>
const price={
 "Serenity Beach Pavilion":{ "3hr":1275,"7hr":2550 },
 "Paradise Palms Pavilion":{ "3hr":1350,"7hr":2700 },
 "Celebration Lawn":{ "3hr":1275,"7hr":2550 },
 "Small Pavilion":{ "3hr":250,"7hr":500 },
 "Splash Pad Pavilion":{ "3hr":400,"7hr":800 },
 "Meeting Room":{ "3hr":650,"early":1050,"late":1650 },
 "Meeting Room + Patio":{ "early":2300,"late":3400 },
 "Castle Hall":{ "early":5000,"late":7000,"fullday":10000 }
};

function calc(){
  const v=document.getElementById('venue').value;
  const t=document.getElementById('time').value;
  const mem=+document.getElementById('mem').value||0;
  const non=+document.getElementById('non').value||0;
  const hrs=+document.getElementById('hrs').value||0;
  const base=price[v]?.[t]??0;
  const total=base+(mem*10)+(non*20)+(hrs*200);
  document.getElementById('total').textContent=total?`$${total.toLocaleString()}`:'$0.00';
}
['venue','time','mem','non','hrs'].forEach(id=>document.getElementById(id).addEventListener('input',calc));
</script>
<!-- =========================================================== -->
