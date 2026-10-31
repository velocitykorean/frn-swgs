# Fern Swings YouTube Automation Bot 🪺🐣

A fully automated production pipeline for the **FernSwings** nature channel (*Little Wings, Hidden Wonders*) — beautiful hummingbirds, hidden nests, baby birds, and peaceful forest scenes.

## Channel

**Welcome to FernSwings — Little Wings, Hidden Wonders.**

Step into the beautiful world of nature, where tiny birds, hidden nests, and extraordinary wildlife moments reveal the magic of life.

What you'll discover here: beautiful birds and hummingbirds, amazing nests and precious moments of birdlife, peaceful forests and enchanting nature scenes, fascinating wildlife and animal behavior — heartwarming, relaxing, and visually stunning nature videos.

**FernSwings — Little Wings. Hidden Wonders.**

`#FernSwings #Wildlife #Birds #Nature #Hummingbirds`

## Architecture

```
frn-swgs/
├── .env                        # Environment configuration & Google Drive folder IDs
├── google_drive_fetch.py       # Downloads Video, Audio, Image triplets from Google Drive
├── thumbnail_generator.py      # Creates hummingbird-themed high-CTR thumbnails
├── video_generator.py          # Removes watermarks, builds seamless ping-pong loops & syncs audio
├── auto_pipeline.py            # Master end-to-end automation orchestrator
├── publish_youtube.py          # YouTube Data API upload module (Fern Swings channel)
├── published_videos.json       # Publication history tracking
├── input_videos/               # Local / synced hummingbird & nature video loops (MP4/MOV)
├── input_audio/                # Local / synced ambient relaxation music tracks (MP3/WAV)
├── input_images/               # Local / synced hummingbird & nest thumbnail backgrounds
├── output_thumbnails/          # Generated YouTube thumbnails (1280x720)
└── output_videos/              # Rendered 1080p full-length videos (1 Hour)
```

## Configuration (`.env`)

Add your Google Drive Folder IDs in `.env`:

```env
# Google Drive Folder IDs (Fern Swings)
GOOGLE_DRIVE_VIDEO_FOLDER_ID=1Jrgvbd8SuBlHaPIbs8PFxm7VeuyY9BKM
GOOGLE_DRIVE_AUDIO_FOLDER_ID=your_audio_folder_id_here
GOOGLE_DRIVE_IMAGE_FOLDER_ID=1aWeuTd_NOV5VYGucAdUoHs7LJuZdEJLF

# Google Service Account Key
GOOGLE_SERVICE_ACCOUNT_KEY=service_account.json
```

> **Note:** Share each of your 3 Google Drive folders with the Service Account email in `service_account.json` with **Viewer** access.

## Usage Commands

### 1. Run Complete Automation Pipeline (1-Hour Video)

```powershell
python auto_pipeline.py --duration 3600
```

### 2. Run Preview Test (5-Minute Video Dry-Run)

```powershell
python auto_pipeline.py --duration 300 --dry-run
```

### 3. Generate Thumbnail Only

```powershell
python thumbnail_generator.py
```
