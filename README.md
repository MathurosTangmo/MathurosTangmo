<html lang="th">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>StarTrack DEMO</title>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;500;600;700&amp;display=swap" rel="stylesheet">
  <style>
      body {
        box-sizing: border-box;
        font-family: 'Sarabun', Arial, sans-serif;
        background: linear-gradient(135deg, #f4eaff, #d3ecfd);
        color: #444;
        margin: 0;
        height: 100%;
        width: 100%;
      }
      html {
        height: 100%;
        width: 100%;
      }
      
      header {
        text-align: center;
        background: #fcecfb;
        border-bottom: 2px solid #e5d9f7;
        padding: 1.7em 1em 0.3em 1em;
      }
      h1 {
        color: #a645ae;
        margin: 0.5em 0 0.1em 0;
        font-size: 2em;
        font-weight: bold;
      }
      .tagline {
        color: #7193a6;
        font-size: 0.9em;
        margin: 0.3em 0 1em 0;
      }
      
      nav {
        text-align: center;
        padding: 1.1em;
        background: #f2f7fd;
      }
      
      .rolebtn {
        background: #e9dfff;
        color: #86398e;
        font-size: 1.19em;
        border: none;
        border-radius: 11px;
        padding: 0.8em 2.2em;
        margin: 0.4em;
        cursor: pointer;
        transition: background 0.2s;
      }
      .rolebtn:hover,
      .rolebtn.active {
        background: #d4c5f5;
      }
      
      section {
        max-width: 930px;
        margin: 2em auto;
        background: #fffefe;
        border-radius: 23px;
        padding: 2em 2.2em;
        box-shadow: 0 4px 25px #e4eaf4cc;
      }
      h2 {
        color: #a645ae;
        margin-top: 0;
        letter-spacing: 0.03em;
        font-weight: bold;
        font-size: 1.5em;
        margin-bottom: 0.8em;
      }
      
      .box {
        background: #f7f9fd;
        border-radius: 15px;
        padding: 1.35em 2em;
        margin-bottom: 2em;
        box-shadow: 0 1px 18px #e7e1fa60;
      }
      .box h3 {
        color: #7193a6;
        font-weight: bold;
        font-size: 1.2em;
        margin-bottom: 1em;
        display: flex;
        align-items: center;
        gap: 8px;
      }
      
      .star {
        color: #ffe780;
        font-size: 1.4em;
        text-shadow: 0 0 1px #dcbba0;
      }
      .good {
        color: #399d2f;
      }
      .bad {
        color: #d04a6a;
      }
      
      .stats-table {
        margin-top: 0.7em;
        width: 100%;
        background: #f2f7fd;
        border-collapse: collapse;
      }
      .stats-table th,
      .stats-table td {
        border: 1px solid #ccc;
        padding: 0.5em 0.7em;
        text-align: left;
      }
      .stats-table th {
        background: #f9e3ff;
        color: #86398e;
        font-weight: bold;
      }
      
      .emotion-btns {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: 5px;
      }
      .emotion-btns button {
        margin: 0.4em 0.13em;
        font-size: 1.5em;
        padding: 0.2em 0.5em;
        border-radius: 50%;
        border: 1.3px solid #b6c5ee;
        background: #e6f6ff;
        cursor: pointer;
        transition: transform 0.1s;
      }
      .emotion-btns button.selected,
      .emotion-btns button:hover {
        background: #ffd7ef;
        border-color: #bb5ecf;
        transform: scale(1.1);
      }
      
      textarea,
      select,
      input[type='text'],
      input[type='number'],
      input[type='datetime-local'] {
        width: 100%;
        padding: 0.7em;
        margin: 0.3em 0 1em 0;
        border-radius: 7px;
        border: 1.25px solid #d3ecfd;
        background: #fff6f8;
        outline: none;
        color: #555;
        font-family: 'Sarabun', Arial, sans-serif;
        box-sizing: border-box;
      }
      
      .btn-main,
      .test-btn,
      .appoint-btn {
        background: #a651b1;
        color: #fff;
        border: none;
        border-radius: 9px;
        font-weight: bold;
        font-size: 1.07em;
        padding: 0.7em 2em;
        margin: 0.8em 0;
        box-shadow: 0 1px 7px #ede0fb40;
        cursor: pointer;
        display: inline-flex;
        align-items: center;
        justify-content: center;
        gap: 8px;
      }
      .btn-main:hover,
      .test-btn:hover,
      .appoint-btn:hover {
        background: #e6c6f5;
        color: #640a73;
      }
      
      .hidden {
        display: none;
      }
      
      .log-item {
        background: #fff;
        padding: 1em;
        margin: 0.5em 0;
        border-radius: 8px;
        border-left: 4px solid #a645ae;
      }
      
      .test-result {
        background: #e8f5e9;
        padding: 1.5em;
        margin: 1em 0;
        border-radius: 10px;
        border: 2px solid #66bb6a;
      }
      
      .appointment-item {
        background: #fff3e0;
        padding: 1em;
        margin: 0.5em 0;
        border-radius: 8px;
        border-left: 4px solid #ff9800;
      }
    </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body>
  <header>
   <h1 id="app-title">StarTrack DEMO</h1>
   <p class="tagline" id="tagline">ติดตามดาวของคุณ</p>
  </header>
  <nav><button class="rolebtn active" data-role="patient">ผู้ป่วย</button> <button class="rolebtn" data-role="doctor">แพทย์</button> <button class="rolebtn" data-role="family">ญาติ</button>
  </nav><!-- ส่วนผู้ป่วย -->
  <section id="patient-section">
   <h2>📋 บันทึกอาการประจำวัน</h2>
   <div class="box">
    <h3><span class="star">⭐</span> ความรู้สึกวันนี้</h3>
    <div class="emotion-btns"><button data-emotion="😊">😊</button> <button data-emotion="😐">😐</button> <button data-emotion="😢">😢</button> <button data-emotion="😰">😰</button> <button data-emotion="😡">😡</button>
    </div>
   </div>
   <div class="box">
    <h3>🗒️ บันทึกอาการ</h3><label for="symptom-text">รายละเอียดอาการ:</label> <textarea id="symptom-text" rows="4" placeholder="เช่น ปวดหัว นอนไม่หลับ เครียด..."></textarea> <label for="symptom-level">ระดับความรุนแรง (1-10):</label> <input type="number" id="symptom-level" min="1" max="10" value="5"> <button class="btn-main" id="save-log-btn">💾 บันทึก</button>
   </div>
   <div class="box">
    <h3>📊 ประวัติการบันทึก</h3>
    <div id="log-history"></div>
   </div>
   <div class="box">
    <h3>🧪 ทำแบบทดสอบ</h3>
    <p>ทำแบบประเมินอาการทางจิตเวช</p><button class="test-btn" id="start-test-btn">เริ่มทำแบบทดสอบ</button>
    <div id="test-area" class="hidden">
     <h4 style="color: #7193a6; margin-top: 1em;">คำถามตัวอย่าง:</h4>
     <p><strong>1. คุณรู้สึกเศร้าหรือหดหู่บ่อยแค่ไหน?</strong></p><select id="q1"> <option value="0">ไม่เลย</option> <option value="1">บางครั้้ง</option> <option value="2">บ่อยครั้ง</option> <option value="3">เกือบตลอดเวลา</option> </select>
     <p><strong>2. คุณสนใจทำกิจกรรมที่เคยชอบหรือไม่?</strong></p><select id="q2"> <option value="0">สนใจเหมือนเดิม</option> <option value="1">สนใจน้อยลง</option> <option value="2">แทบไม่สนใจ</option> <option value="3">ไม่สนใจเลย</option> </select>
     <p><strong>3. คุณมีปัญหาการนอนหลับหรือไม่?</strong></p><select id="q3"> <option value="0">ไม่มีปัญหา</option> <option value="1">นอนยากบ้าง</option> <option value="2">นอนยากบ่อย</option> <option value="3">นอนไม่หลับเกือบทุกคืน</option> </select> <button class="btn-main" id="submit-test-btn">ส่งคำตอบ</button>
    </div>
    <div id="test-results"></div>
   </div>
   <div class="box">
    <h3>📅 นัดหมายแพทย์</h3><label for="appoint-date">วันที่และเวลา:</label> <input type="datetime-local" id="appoint-date"> <label for="appoint-note">หมายเหตุ:</label> <input type="text" id="appoint-note" placeholder="เช่น ตรวจติดตาม..."> <button class="appoint-btn" id="save-appointment-btn">📅 บันทึกนัดหมาย</button>
    <div id="appointment-list" style="margin-top: 1em;"></div>
   </div>
  </section><!-- ส่วนแพทย์ -->
  <section id="doctor-section" class="hidden">
   <h2>👨‍⚕️ แดชบอร์ดแพทย์</h2>
   <div class="box">
    <h3>📈 สถิติผู้ป่วย</h3>
    <table class="stats-table">
     <thead>
      <tr>
       <th>ชื่อผู้ป่วย</th>
       <th>อาการล่าสุด</th>
       <th>ระดับ</th>
       <th>สถานะ</th>
      </tr>
     </thead>
     <tbody>
      <tr>
       <td>คุณสมชาย ใจดี</td>
       <td>ปวดหัว เครียด</td>
       <td>7/10</td>
       <td><span class="bad">⚠️ ต้องติดตาม</span></td>
      </tr>
      <tr>
       <td>คุณสมหญิง สุขใจ</td>
       <td>นอนไม่หลับ</td>
       <td>5/10</td>
       <td><span class="good">✅ ปกติ</span></td>
      </tr>
      <tr>
       <td>คุณสมศักดิ์ มีสุข</td>
       <td>วิตกกังวล</td>
       <td>8/10</td>
       <td><span class="bad">🔴 เร่งด่วน</span></td>
      </tr>
     </tbody>
    </table>
   </div>
   <div class="box">
    <h3>📝 เขียนใบสั่งยา</h3><label for="patient-name">ชื่อผู้ป่วย:</label> <input type="text" id="patient-name" placeholder="ระบุชื่อ"> <label for="medication">ยาที่สั่ง:</label> <textarea id="medication" rows="3" placeholder="เช่น Sertraline 50mg วันละ 1 เม็ด..."></textarea> <label for="doctor-note">คำแนะนำ:</label> <textarea id="doctor-note" rows="2" placeholder="คำแนะนำเพิ่มเติม..."></textarea> <button class="btn-main" id="save-prescription-btn">💊 บันทึกใบสั่งยา</button>
    <div id="prescription-result" style="margin-top: 1em;"></div>
   </div>
  </section><!-- ส่วนญาติ -->
  <section id="family-section" class="hidden">
   <h2>👨‍👩‍👧 พื้นที่สำหรับญาติ</h2>
   <div class="box">
    <h3>💚 ข้อมูลผู้ป่วย</h3>
    <p><strong>ชื่อผู้ป่วย:</strong> คุณสมชาย ใจดี</p>
    <p><strong>อาการล่าสุด:</strong> ปวดหัว เครียด (ระดับ 7/10)</p>
    <p><strong>การนัดหมายถัดไป:</strong> 15 มกราคม 2567 เวลา 14:00 น.</p>
   </div>
   <div class="box">
    <h3>📚 ความรู้เกี่ยวกับโรคทางจิตเวช</h3>
    <ul style="line-height: 1.8;">
     <li><strong>โรคซึมเศร้า:</strong> อาการเศร้าหม่นหมอง ไม่สนใจกิจกรรม นอนไม่หลับ</li>
     <li><strong>โรควิตกกังวล:</strong> กังวลมากเกินไป หายใจไม่สะดวก หัวใจเต้นเร็ว</li>
     <li><strong>การดูแลผู้ป่วย:</strong> รับฟัง ให้กำลังใจ ไม่ตำหนิ พาพบแพทย์สม่ำเสมอ</li>
    </ul>
   </div>
   <div class="box">
    <h3>✉️ ส่งข้อความให้กำลังใจ</h3><label for="support-message">ข้อความ:</label> <textarea id="support-message" rows="3" placeholder="เขียนข้อความให้กำลังใจผู้ป่วย..."></textarea> <button class="btn-main" id="send-support-btn">📨 ส่งข้อความ</button>
    <div id="support-result" style="margin-top: 1em;"></div>
   </div>
  </section>
  <script>
      const defaultConfig = {
        app_title: 'StarTrack DEMO',
        tagline: 'ติดตามดาวของคุณ'
      };

      let config = { ...defaultConfig };

      // State management
      let currentRole = 'patient';
      let selectedEmotion = null;
      let logs = [];
      let appointments = [];

      // Role switching
      const roleButtons = document.querySelectorAll('.rolebtn');
      const sections = {
        patient: document.getElementById('patient-section'),
        doctor: document.getElementById('doctor-section'),
        family: document.getElementById('family-section')
      };

      roleButtons.forEach((btn) => {
        btn.addEventListener('click', () => {
          const role = btn.dataset.role;
          currentRole = role;

          roleButtons.forEach((b) => b.classList.remove('active'));
          btn.classList.add('active');

          Object.keys(sections).forEach((key) => {
            sections[key].classList.add('hidden');
          });
          sections[role].classList.remove('hidden');
        });
      });

      // Emotion selection
      const emotionButtons = document.querySelectorAll('.emotion-btns button');
      emotionButtons.forEach((btn) => {
        btn.addEventListener('click', () => {
          emotionButtons.forEach((b) => b.classList.remove('selected'));
          btn.classList.add('selected');
          selectedEmotion = btn.dataset.emotion;
        });
      });

      // Save symptom log
      document.getElementById('save-log-btn').addEventListener('click', () => {
        const symptomText = document.getElementById('symptom-text').value;
        const symptomLevel = document.getElementById('symptom-level').value;

        if (!symptomText.trim()) {
          showMessage('กรุณากรอกรายละเอียดอาการ', 'warning');
          return;
        }

        const log = {
          id: Date.now(),
          date: new Date().toLocaleString('th-TH'),
          emotion: selectedEmotion || '😐',
          symptom: symptomText,
          level: symptomLevel
        };

        logs.unshift(log);
        displayLogs();
        
        document.getElementById('symptom-text').value = '';
        document.getElementById('symptom-level').value = '5';
        emotionButtons.forEach((b) => b.classList.remove('selected'));
        selectedEmotion = null;

        showMessage('✅ บันทึกอาการเรียบร้อยแล้ว', 'success');
      });

      function displayLogs() {
        const container = document.getElementById('log-history');
        if (logs.length === 0) {
          container.innerHTML = '<p style="color: #999;">ยังไม่มีการบันทึก</p>';
          return;
        }

        container.innerHTML = logs
          .map(
            (log) => `
          <div class="log-item">
            <div style="display: flex; justify-content: space-between; align-items: center;">
              <span style="font-size: 1.3em;">${log.emotion}</span>
              <span style="font-size: 0.85em; color: #999;">${log.date}</span>
            </div>
            <p style="margin: 0.5em 0;"><strong>อาการ:</strong> ${log.symptom}</p>
            <p style="margin: 0; color: ${log.level >= 7 ? '#d04a6a' : '#399d2f'};"><strong>ระดับ:</strong> ${log.level}/10</p>
          </div>
        `
          )
          .join('');
      }

      // Test functionality
      document.getElementById('start-test-btn').addEventListener('click', () => {
        document.getElementById('test-area').classList.remove('hidden');
        document.getElementById('test-results').innerHTML = '';
      });

      document.getElementById('submit-test-btn').addEventListener('click', () => {
        const q1 = parseInt(document.getElementById('q1').value);
        const q2 = parseInt(document.getElementById('q2').value);
        const q3 = parseInt(document.getElementById('q3').value);
        
        const totalScore = q1 + q2 + q3;
        let result = '';
        let resultClass = '';
        
        if (totalScore <= 3) {
          result = 'ผลการประเมิน: <strong class="good">ปกติ</strong><br>คะแนน: ' + totalScore + '/9<br>คำแนะนำ: สุขภาพจิตของคุณอยู่ในเกณฑ์ดี';
          resultClass = 'good';
        } else if (totalScore <= 6) {
          result = 'ผลการประเมิน: <strong style="color: #ff9800;">ควรติดตาม</strong><br>คะแนน: ' + totalScore + '/9<br>คำแนะนำ: ควรพักผ่อนให้เพียงพอและปรึกษาแพทย์หากอาการไม่ดีขึ้น';
          resultClass = 'warning';
        } else {
          result = 'ผลการประเมิน: <strong class="bad">ควรพบแพทย์</strong><br>คะแนน: ' + totalScore + '/9<br>คำแนะนำ: ควรปรึกษาแพทย์เฉพาะทางโดยเร็ว';
          resultClass = 'bad';
        }
        
        document.getElementById('test-results').innerHTML = `
          <div class="test-result">
            ${result}
          </div>
        `;
      });

      // Appointment booking
      document.getElementById('save-appointment-btn').addEventListener('click', () => {
        const appointDate = document.getElementById('appoint-date').value;
        const appointNote = document.getElementById('appoint-note').value;

        if (!appointDate) {
          showMessage('กรุณาเลือกวันที่และเวลา', 'warning');
          return;
        }

        const appointment = {
          id: Date.now(),
          date: new Date(appointDate).toLocaleString('th-TH'),
          note: appointNote || 'ไม่มีหมายเหตุ'
        };

        appointments.unshift(appointment);
        displayAppointments();

        document.getElementById('appoint-date').value = '';
        document.getElementById('appoint-note').value = '';

        showMessage('✅ บันทึกนัดหมายเรียบร้อยแล้ว', 'success');
      });

      function displayAppointments() {
        const container = document.getElementById('appointment-list');
        if (appointments.length === 0) {
          container.innerHTML = '<p style="color: #999;">ยังไม่มีนัดหมาย</p>';
          return;
        }

        container.innerHTML = appointments
          .map(
            (appt) => `
          <div class="appointment-item">
            <p style="margin: 0;"><strong>📅 ${appt.date}</strong></p>
            <p style="margin: 0.5em 0 0 0;">หมายเหตุ: ${appt.note}</p>
          </div>
        `
          )
          .join('');
      }

      // Doctor section
      document.getElementById('save-prescription-btn').addEventListener('click', () => {
        const patientName = document.getElementById('patient-name').value;
        const medication = document.getElementById('medication').value;
        const doctorNote = document.getElementById('doctor-note').value;

        if (!patientName.trim() || !medication.trim()) {
          showMessage('กรุณากรอกข้อมูลให้ครบถ้วน', 'warning');
          return;
        }

        document.getElementById('prescription-result').innerHTML = `
          <div class="test-result">
            <strong>✅ บันทึกใบสั่งยาสำเร็จ</strong><br>
            ผู้ป่วย: ${patientName}<br>
            ยาที่สั่ง: ${medication}<br>
            คำแนะนำ: ${doctorNote || 'ไม่มี'}
          </div>
        `;

        document.getElementById('patient-name').value = '';
        document.getElementById('medication').value = '';
        document.getElementById('doctor-note').value = '';
      });

      // Family section
      document.getElementById('send-support-btn').addEventListener('click', () => {
        const message = document.getElementById('support-message').value;

        if (!message.trim()) {
          showMessage('กรุณาเขียนข้อความ', 'warning');
          return;
        }

        document.getElementById('support-result').innerHTML = `
          <div class="test-result">
            <strong>✅ ส่งข้อความเรียบร้อยแล้ว</strong><br>
            "${message}"
          </div>
        `;

        document.getElementById('support-message').value = '';
      });

      function showMessage(message, type) {
        const container = document.createElement('div');
        container.style.cssText = `
          position: fixed;
          top: 20px;
          left: 50%;
          transform: translateX(-50%);
          background: ${type === 'success' ? '#4caf50' : '#ff9800'};
          color: white;
          padding: 1em 2em;
          border-radius: 10px;
          box-shadow: 0 4px 15px rgba(0,0,0,0.2);
          z-index: 1000;
          font-weight: bold;
        `;
        container.textContent = message;
        document.body.appendChild(container);

        setTimeout(() => {
          container.remove();
        }, 3000);
      }

      // Element SDK Integration
      async function onConfigChange(newConfig) {
        document.getElementById('app-title').textContent = newConfig.app_title || defaultConfig.app_title;
        document.getElementById('tagline').textContent = newConfig.tagline || defaultConfig.tagline;
      }

      if (window.elementSdk) {
        window.elementSdk.init({
          defaultConfig,
          onConfigChange,
          mapToCapabilities: (config) => ({
            recolorables: [],
            borderables: [],
            fontEditable: undefined,
            fontSizeable: undefined
          }),
          mapToEditPanelValues: (config) =>
            new Map([
              ['app_title', config.app_title || defaultConfig.app_title],
              ['tagline', config.tagline || defaultConfig.tagline]
            ])
        });
      }

      // Initialize
      displayLogs();
      displayAppointments();
    </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9a6169077365b4cd',t:'MTc2NDQxMjAyMy4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
