# TrikMed Voice Recorder

## Local Run
```bash
pip install -r requirements.txt
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```
Open: http://localhost:8000

## Server Deploy (Ubuntu)
```bash
sudo apt update && sudo apt install python3-pip python3-venv -y
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
mkdir -p recordings
```

### Run with nohup (stays running after logout)
```bash
nohup uvicorn main:app --host 0.0.0.0 --port 8000 > app.log 2>&1 &
```

### Or use systemd service (recommended)
```bash
# Copy trikmed-recorder.service to /etc/systemd/system/
sudo systemctl enable trikmed-recorder
sudo systemctl start trikmed-recorder
```

## Recordings
- Audio files: `./recordings/*.webm`
- Database: `./trikmed.db` (SQLite)
- Admin API: `GET /api/admin/recordings`
