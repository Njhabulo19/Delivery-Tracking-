<!doctype html>

<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Parcel Delivery Details</title>
  <style>
    body{font-family:Arial,sans-serif;background:#f7f7fb;color:#111;margin:0;padding:0}
    .container{max-width:700px;margin:50px auto;padding:20px;background:#fff;border-radius:12px;box-shadow:0 6px 18px rgba(0,0,0,0.06)}
    h1{margin-top:0;font-size:22px}
    input, button{padding:10px;font-size:15px;border-radius:8px;border:1px solid #ccc}
    input{width:70%}
    button{width:25%;background:#0b63d6;color:#fff;border:none;cursor:pointer}
    .result{margin-top:20px;padding:15px;border-radius:8px;background:#fbfdff;border:1px solid #e8f0ff}
    .error{background:#fff2f2;border:1px solid #ffd2d2;color:#9b1c1c}
    .field{margin:6px 0}
    .label{font-weight:700;color:#0b63d6}
    iframe{width:100%;height:300px;border:0;margin-top:10px;border-radius:8px}
  </style>
</head>
<body>
  <div class="container">
    <h1>Parcel Delivery Tracker</h1>
    <p>Enter the exact parcel number to see delivery details and location.</p><input type="text" id="waybill" placeholder="e.g. CG123456789">
<button id="checkBtn">Check Parcel</button>

<div id="output" class="result" style="display:none"></div>

  </div>  <script>
    const MOCK = {
      'CG123456789': {
        waybill: 'CG123456789',
        status: 'Out for delivery',
        scheduled_delivery: '25/09/2025',
        from: 'Johannesburg',
        to: 'PEP Selgro Centre, Shop 29, Corner Church & Boshoff Street, Pietermaritzburg, KwaZulu-Natal',
        client: 'Lungelo Bongani Khethwa Nxumalo',
        contact: '078 214 3503',
        map: 'https://www.google.com/maps?q=PEP+Selgro+Centre,+Shop+29,+Corner+Church+%26+Boshoff+Street,+Pietermaritzburg&output=embed'
      }
    };

    const waybillInput = document.getElementById('waybill');
    const checkBtn = document.getElementById('checkBtn');
    const output = document.getElementById('output');

    function sanitizeInput(s){ return String(s||'').trim().toUpperCase(); }

    function showMessage(html, isError){
      output.style.display = 'block';
      output.className = isError ? 'result error' : 'result';
      output.innerHTML = html;
    }

    function checkParcel(){
      const waybill = sanitizeInput(waybillInput.value);
      if(!waybill){ showMessage('Please enter a parcel number.', true); return; }

      if(MOCK[waybill]){
        const p = MOCK[waybill];
        showMessage(`
          <div class="field"><span class="label">Waybill:</span> ${p.waybill}</div>
          <div class="field"><span class="label">Status:</span> ${p.status}</div>
          <div class="field"><span class="label">Scheduled Delivery:</span> ${p.scheduled_delivery}</div>
          <div class="field"><span class="label">From:</span> ${p.from}</div>
          <div class="field"><span class="label">To:</span> ${p.to}</div>
          <div class="field"><span class="label">Client:</span> ${p.client}</div>
          <div class="field"><span class="label">Contact:</span> ${p.contact}</div>
          <iframe src="${p.map}" loading="lazy"></iframe>
        `, false);
      } else {
        showMessage('Parcel number not found. Please check and try again.', true);
      }
    }

    checkBtn.addEventListener('click', checkParcel);
    waybillInput.addEventListener('keydown', (e)=>{ if(e.key==='Enter') checkParcel(); });
  </script></body>
</html>
