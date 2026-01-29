# ALERA

ALERA is a web application that provides image-based disease/skin analysis using a trained ML model. The repository contains the web frontend (HTML/CSS/JS), a Python backend (Flask) for model inference and training helpers, example/test images, and deployment helpers (Dockerfile, Procfile).

> Note: This README was drafted by inspecting the repository files. Check `.env.example` and `requirements.txt` for exact runtime dependencies and environment variables.

## Project layout (observed)
- app.py — Python backend (Flask) and inference endpoints
- server.js — Node server (static server / alternative deployment)
- train_model.py — script for training the model
- models/ — directory for storing trained model files (place model files here)
- static/ — static assets (CSS, JS, images)
- *.html — frontend pages (index.html, login.html, signup.html, results.html, uploadDNAimage.html, about.html, contact.html, allergy.html, etc.)
- requirements.txt — Python dependencies
- package.json / package-lock.json — Node/npm metadata
- Dockerfile — container setup
- Procfile / runtime.txt — deployment hints (Heroku)
- .env.example — example environment variables
- test_*.jpg — sample images for quick testing

## Features
- Upload images via the web UI for model inference
- Backend inference endpoints in Python (see `app.py`)
- Training helper script (`train_model.py`) to build or update the model
- Static frontend pages for user interaction and result display
- Example/test images included for quick manual testing

## Quick start (local)
1. Clone the repo
   git clone https://github.com/Midhungirish2002/ALERA.git
   cd ALERA

2. Python environment
   - Create and activate a virtual environment (recommended)
     python3 -m venv venv
     source venv/bin/activate  # macOS / Linux
     venv\Scripts\activate     # Windows
   - Install Python packages
     pip install -r requirements.txt

3. Environment variables
   - Copy `.env.example` to `.env` and fill in the required values
     cp .env.example .env

4. Place model files
   - Put any trained model files into the `models/` directory (the app looks for model artifacts there).

5. Run the app
   - Development with Flask:
     python app.py
     Open http://localhost:5000 (or the address printed by app)
   - Alternatively, if you prefer using the Node static server:
     npm install
     node server.js
     Open http://localhost:5000 (or the port in server.js)

## Training a model
- Use `train_model.py` to train or fine-tune models. The precise CLI/arguments depend on the script internals — check the top of `train_model.py` for usage details.
- After training, save the model artifacts into `models/` so that the Flask app can load them for inference.

## Deployment
- Docker: A `Dockerfile` is provided for container builds. Example:
  docker build -t alera .
  docker run -p 5000:5000 alera
- Heroku: `Procfile` and `runtime.txt` exist; adapt the Procfile to your chosen server (e.g., gunicorn or node) and set required environment variables in Heroku config.

## Testing
- Sample images (`test_*.jpg`) are included for manual testing with the upload page or direct API calls.
- Use your browser to upload via the UI pages (e.g., `uploadDNAimage.html` or the index page).

## Environment variables
- See `.env.example` for the variables the app expects (API keys, secrets, model names, etc.). Ensure these are set before starting the app.

## Notes & TODOs
- Confirm whether the production entrypoint is `app.py` (Flask) or `server.js` (Node static). Update `Procfile` accordingly for deployment.
- Add CI / automated tests.
- Add clearer training instructions and expected model file names/paths in `models/`.

## Contributing
Contributions are welcome. Please open issues or PRs for bug fixes, feature requests, and documentation improvements.

## License
Add a LICENSE file or state the license you want to use. (No license file was found in the repository when this README was drafted.)

## Contact
For questions or help, open an issue or contact the repository owner.
