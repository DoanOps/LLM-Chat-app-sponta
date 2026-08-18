# Matches the playwright version pinned in pyproject.toml — the Playwright
# Python package and the installed browser build must stay in lockstep, and
# this base image ships both together with all of Chromium's OS dependencies
# already installed (the part that's fiddly to do by hand on Amazon Linux).
FROM mcr.microsoft.com/playwright/python:v1.60.0-noble

WORKDIR /app

COPY pyproject.toml ./
COPY app ./app

RUN pip install --no-cache-dir -e .

EXPOSE 8008

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8008"]
