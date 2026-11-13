# Python CI Project

A simple Python calculator project with Continuous Integration using GitHub Actions.

## What the CI pipeline does
Every push or pull request to `main` automatically:
1. Installs dependencies
2. Lints the code (flake8)
3. Runs tests (pytest)
4. Generates and uploads a test report

## Run locally
```
pip install -r requirements.txt
flake8 . --max-line-length=100
pytest -v
```

## Trigger the pipeline
Push any commit to the `main` branch:
```
git add .
git commit -m "Update"
git push
```
Then open the **Actions** tab on GitHub to see the result.

## Replicate this setup
1. Copy `.github/workflows/ci.yml` into your own repo
2. Add `requirements.txt` with pytest and flake8
3. Push to GitHub. The pipeline runs automatically.

## Challenges faced
- pytest.exe was blocked by an Application Control policy on Windows. Fixed by running `python -m pytest`.
- flake8 reported W292 and W293 (missing newline and trailing whitespace). Fixed by cleaning the files.
- Git authentication while pushing to GitHub.

## Notes
CI keeps code quality high by catching errors on every commit.

## View CI logs
1. Open the repository on GitHub
2. Click the **Actions** tab
3. Click a workflow run, then click the **build** job
4. Expand any step (Lint, Run tests) to read its log
5. Download the **test-report** artifact at the bottom of the run page

## How the pipeline ensures quality
If flake8 finds a style error or any pytest test fails, the pipeline stops and the run is marked with a red X. Only code that passes both checks gets a green tick.