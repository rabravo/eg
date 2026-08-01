# ab_audio_trans-cribe-late.py

transcribe a local audio file (interactive mode menu)

    ./ab_audio_trans-cribe-late.py ~/Music/song.mp3 --language ja


specify a faster model

    ./ab_audio_trans-cribe-late.py ~/Music/song.mp3 --language it --model medium


download audio from YouTube and process (skips the YouTube prompt)

    ./ab_audio_trans-cribe-late.py --url "https://www.youtube.com/watch?v=VIDEO_ID" --language ja


no arguments — prompts for audio source then shows mode menu

    ./ab_audio_trans-cribe-late.py


# Modes (chosen interactively)

    1  Transcription in original language  →  stdout + <stem>_transcription.txt
    2  English translation                 →  stdout + <stem>_translation.txt
    3  Both (original + translation)       →  <stem>_transcription.txt + <stem>_translation.txt + <stem>.html


# Notes

requires conda env yt-transcribe to be active:

    conda activate yt-transcribe

all output files are written to the current working directory.

model sizes: tiny / base / small (fast) · medium (balanced) · large / large-v3 (best, default)

supported language codes: ja ko zh fr it es de pt ru ar hi (and many more)
