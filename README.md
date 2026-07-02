# Mark-XLVII Thai BossAgis

JARVIS ภาษาไทยสำหรับทดลองต่อยอดจากโปรเจกต์ Mark-XLVII โดยเพิ่ม prompt ภาษาไทย, config ภาษาไทย, safe mode, command mapping ภาษาไทย และโหมดงาน วพอ.

> ใช้สำหรับเรียนรู้/ทดลองส่วนตัวก่อนนำไปต่อยอดจริง ห้าม commit API key, token, password, cert/key หรือข้อมูลราชการ/ข้อมูลส่วนบุคคลขึ้น GitHub

## จุดที่เพิ่มให้

- `core/prompt.txt` — prompt ภาษาไทยสำหรับ JARVIS
- `config/api_keys.example.th.json` — ตัวอย่าง config ภาษาไทยแบบไม่ใส่ key จริง
- `requirements_thai_safe.txt` — dependency ที่เติมสำหรับภาษาไทย/เสียง/GUI
- `sanity_check_th.py` — ตรวจความพร้อมก่อนรัน
- `tools/thai_command_map.py` — mapping คำสั่งไทยเป็น intent
- `docs/THAI_TEST_COMMANDS.md` — ชุดคำสั่งทดสอบภาษาไทย
- `docs/RTAFNC_WORK_MODE_TH.md` — แนวทางโหมดงาน วพอ.
- `run_jarvis_th_windows.bat` และ `run_jarvis_th_mac_linux.sh` — คำสั่งรันแบบเร็ว

## วิธีติดตั้ง Windows

```powershell
py -3.11 -m venv .venv
.\.venv\Scripts\activate
python -m pip install --upgrade pip setuptools wheel
pip install -r requirements_thai_safe.txt
python -m playwright install chromium
python sanity_check_th.py
python main.py
```

## วิธีติดตั้ง macOS / Linux

```bash
python3.11 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip setuptools wheel
pip install -r requirements_thai_safe.txt
python -m playwright install chromium
python sanity_check_th.py
python main.py
```

## ตั้งค่า API key

คัดลอกไฟล์ตัวอย่าง:

```bash
cp config/api_keys.example.th.json config/api_keys.json
```

แล้วแก้ `config/api_keys.json` ใส่ Gemini API key จริงในเครื่องตัวเองเท่านั้น ห้ามอัปไฟล์นี้ขึ้น GitHub

## คำสั่งทดสอบ

```text
จาร์วิส ได้ยินไหม ตอบภาษาไทย
จาร์วิส เช็กสถานะเครื่องให้หน่อย
จาร์วิส เปิดเว็บ google.com
จาร์วิส ค้นเว็บเรื่อง วิทยาลัยพยาบาลทหารอากาศ
จาร์วิส ดูหน้าจอแล้วบอกว่ามีอะไร
จาร์วิส เปิดโหมดงาน วพอ.
```

## กฎความปลอดภัย

คำสั่งต่อไปนี้ต้องถามยืนยันก่อนเสมอ:

- ลบไฟล์/เขียนทับไฟล์
- ส่งข้อความหรืออีเมล
- กด submit ฟอร์มสำคัญ
- รัน terminal/shell command
- shutdown/restart/lock เครื่อง
- จัดการข้อมูลส่วนบุคคล นักเรียน บุคลากร หรือเอกสารราชการ

## ไฟล์ที่ไม่ควรอยู่ใน repo

`.gitignore` ตั้งไว้ให้กันไฟล์เสี่ยงแล้ว เช่น:

- `config/api_keys.json`
- `.env`
- `*.key`, `*.crt`, `*.pem`
- `__pycache__/`, `*.pyc`
- `.venv/`
