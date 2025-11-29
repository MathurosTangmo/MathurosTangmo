<html lang="th">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>StarTrack DEMO</title>

    <!-- Tailwind -->
    <script src="https://cdn.tailwindcss.com"></script>

    <!-- ฟอนต์ Sarabun -->
    <link
      href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;500;600;700&display=swap"
      rel="stylesheet"
    />

    <style>
      body {
        font-family: 'Sarabun', Arial, sans-serif;
        background: linear-gradient(135deg,#f4eaff,#d3ecfd);
        color: #444;
        margin: 0;
        min-height: 100vh;
      }
      header {
        text-align: center;
        background: #fcecfb;
        border-bottom:2px solid #e5d9f7;
        padding-top:1.7em; padding-bottom:.3em;
      }
      h1 { color: #a645ae; margin:0.5em 0 .1em 0; font-size: 2em; font-weight: bold; }
      nav { text-align:center; padding:1.1em; background:#f2f7fd; }
      
      .rolebtn {
        background:#e9dfff;
        color: #86398e;
        font-size:1.19em;
        border:none;
        border-radius:11px;
        padding:.8em 2.2em;
        margin:.4em;
        cursor:pointer;
        transition: background 0.2s;
      }
      .rolebtn:hover, .rolebtn.active { background: #d4c5f5; }
      
      section {
        max-width: 930px;
        margin: 2em auto;
        background: #fffefe;
        border-radius: 23px;
        padding:2em 2.2em;
        box-shadow: 0 4px 25px #e4eaf4cc;
      }
      h2 {
        color:#a645ae;
        margin-top:0;
        letter-spacing:.03em;
        font-weight: bold;
        font-size: 1.5em;
        margin-bottom: 0.8em;
      }
      
      .box {
        background: #f7f9fd;
        border-radius: 15px;
        padding:1.35em 2em;
        margin-bottom:2em;
        box-shadow:0 1px 18px #e7e1fa60;
      }
      .box h3 {
        color:#7193a6;
        font-weight: bold; 
        font-size: 1.2em; 
        margin-bottom: 1em; 
        display: flex; 
        align-items: center; 
        gap: 8px;
      }
      
      .star { color: #ffe780; font-size:1.4em; text-shadow: 0 0 1px #dcbba0; }
      .good {color:#399d2f;}
      .bad {color:#d04a6a;}
      
      .stats-table {
        margin-top: .7em;
        width: 100%;
        background: #f2f7fd;
        border-collapse: collapse;
      }
      .stats-table th, .stats-table td {
        border: 1px solid #ccc;
        padding: .5em .7em;
        text-align: left;
      }
      .stats-table th { background: #f9e3ff; color: #86398e; font-weight: bold;}
      
      .emotion-btns { display: flex; flex-wrap: wrap; justify-content: center; gap: 5px; }
      .emotion-btns button {
        margin:.4em .13em;
        font-size:1.5em;
        padding:.2em .5em;
        border-radius:50%;
        border: 1.3px solid #b6c5ee;
        background:#e6f6ff;
        cursor: pointer;
        transition: transform 0.1s;
      }
      .emotion-btns button.selected,
      .emotion-btns button:hover {
        background:#ffd7ef;
        border-color:#bb5ecf;
        transform: scale(1.1);
      }
      
      textarea, select, input[type="text"], input[type="number"], input[type="datetime-local"] {
        width: 100%;
        padding:.7em;
        margin:.3em 0 1em 0;
        border-radius: 7px;
        border: 1.25px solid #d3ecfd;
        background: #fff6f8;
        outline: none;
        color: #555;
      }
      
      .btn-main, .test-btn, .appoint-btn {
        background: #a651b1;
        color: #fff;
        border: none;
        border-radius: 9px;
        font-weight:bold;
        font-size:1.07em;
        padding:.7em 2em;
        margin:.8em 0;
        box-shadow:0 1px 7px #ede0fb40;
        cursor: pointer;
        display: inline-flex;
        align-items: center;
        justify-content: center;
        gap: 8px;
      }
      .btn-main:hover, .test-btn:hover, .appoint-btn:hover {background:#e6c6f5; color:#640a73;}
      
      .test-btn{background:#b1e5e0;color:#446e67; margin:0 .7em 0 0;}
      .appoint-btn{background:#ffc285;color:#764108;}
      
      .diary-list {margin:1em 0;}
      .diary-entry {
        background: #f3f1fc;
        border-radius:10px;
        margin-bottom:.5em;
        padding:.7em 1em;
        position: relative;
      }
      .diary-date {font-size:.93em; color:#91a;display:block; margin-bottom: 4px;}
      .diary-del-btn {
        float:right;
        background: #ffd7ef;
        color: #d13d84;
        border-radius: 6px;
        padding: .08em .7em;
        cursor: pointer;
        border: none;
      }
      
      .reward-box {
        background: #e6f6ff;
        border-radius:11px;
        padding:1em 1em;
        margin:1em 0;
        color:#608498;
      }
      
      .test-res {
        margin:1em 0;
        background: #d9fff5;
        color:#575;
        border-radius:.7em;
        padding:1em;
      }
      .piebox {text-align:center; background:#f2f7fd; border-radius:12px;margin:1em 0; padding: 1em;}
      .historylist {
        background:#e6f6ff;
        border-radius:10px;
        padding:.8em;
      }
      .msgbox {
        background:#f1ffea;
        padding:1em 1.5em;
        border-radius:10px;
        margin-top:.9em;
      }
      .msg-entry {margin-bottom:.68em;}
      
      /* Reset generic styles */
      .bg-white { background-color: transparent !important; }
      .border { border-width: 0 !important; }
    </style>

    <!-- React 17 UMD + Babel (เหมาะกับ GitHub Pages / แค่ HTML ไฟล์เดียว) -->
    <script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  </head>
  <body>
    <div id="root"></div>

    <!-- โค้ด React เขียนด้วย JSX แปลด้วย Babel บน browser -->
    <script type="text/babel">
      const { useState } = React;

      function App() {
        const [role, setRole] = useState("student");
        const [emotion, setEmotion] = useState("");
        const [diaryText, setDiaryText] = useState("");
        const [diaries, setDiaries] = useState([]);

        const roles = {
          student: "โหมดนักเรียน",
          counselor: "โหมดครูที่ปรึกษา",
          parent: "โหมดผู้ปกครอง",
        };

        const saveDiary = () => {
          const text = diaryText.trim();
          if (!text) return;
          const item = {
            id: Date.now(),
            text,
            time: new Date().toLocaleString("th-TH"),
          };
          setDiaries((prev) => [item, ...prev]);
          setDiaryText("");
        };

        const deleteDiary = (id) => {
          setDiaries((prev) => prev.filter((d) => d.id !== id));
        };

        return (
          <>
            <header>
              <h1>StarTrack DEMO</h1>
              <p style={{ marginTop: 0, marginBottom: "0.4em" }}>
                บันทึกสภาพจิตใจและติดตามการดูแลนักเรียนแบบง่าย ๆ
              </p>
            </header>

            <nav>
              {Object.entries(roles).map(([key, label]) => (
                <button
                  key={key}
                  className={"rolebtn" + (role === key ? " active" : "")}
                  onClick={() => setRole(key)}
                >
                  {label}
                </button>
              ))}
            </nav>

            <section>
              {/* กล่อง 1: อารมณ์วันนี้ */}
              <div className="box">
                <h3>
                  <span className="star">★</span>
                  อารมณ์ของวันนี้
                </h3>
                <div className="emotion-btns">
                  {["😄", "🙂", "😐", "😕", "😭", "😡"].map((icon) => (
                    <button
                      key={icon}
                      className={emotion === icon ? "selected" : ""}
                      onClick={() => setEmotion(icon)}
                    >
                      {icon}
                    </button>
                  ))}
                </div>
                {emotion && (
                  <div className="msgbox">
                    <div className="msg-entry">
                      วันนี้คุณเลือกอารมณ์ <strong>{emotion}</strong>{" "}
                      จุกจิกบันทึกไว้ให้แล้วนะคะ 💜
                    </div>
                  </div>
                )}
              </div>

              {/* กล่อง 2: ไดอารี่ */}
              <div className="box">
                <h3>
                  <span className="star">★</span>
                  ไดอารี่สั้น ๆ วันนี้
                </h3>
                <textarea
                  rows={3}
                  placeholder="วันนี้เกิดอะไรขึ้นบ้าง ที่อยากให้ระบบช่วยจำ..."
                  value={diaryText}
                  onChange={(e) => setDiaryText(e.target.value)}
                />
                <button className="btn-main" onClick={saveDiary}>
                  บันทึกไดอารี่
                </button>

                {diaries.length > 0 && (
                  <div className="diary-list">
                    {diaries.map((item) => (
                      <div key={item.id} className="diary-entry">
                        <span className="diary-date">{item.time}</span>
                        <button
                          className="diary-del-btn"
                          onClick={() => deleteDiary(item.id)}
                        >
                          ลบ
                        </button>
                        <div>{item.text}</div>
                      </div>
                    ))}
                  </div>
                )}
              </div>

              {/* กล่อง 3: สรุปการใช้งาน DEMO */}
              <div className="box">
                <h3>
                  <span className="star">★</span>
                  ภาพรวมการใช้งาน (DEMO)
                </h3>
                <p>
                  โหมดที่เลือกปัจจุบันคือ{" "}
                  <strong>
