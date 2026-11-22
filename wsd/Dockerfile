FROM python:3.12-slim
# Labels für HA
LABEL \
    io.hass.name="WSD4HA_dev" \
    io.hass.description="Registers at a document scanner as a WSD destination to receive and store any scanned documents in HA" \
    io.hass.version="0.1.4" \
    io.hass.type="addon" \
    io.hass.arch="amd64|aarch64"

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY config.yaml .
COPY config.py .
COPY globals.py .
COPY main.py .
COPY parse.py .
COPY scan_job.py .
COPY scanner.py .
COPY send.py .
COPY webserver.py .
COPY templates.py .
COPY tools.py .
COPY translations/en.yaml ./translations
COPY wsd.py .

EXPOSE 8110
EXPOSE 5357
#VOLUME ["/share/scans":"/share/scans"]
VOLUME ["/config/wsd4ha/scans"]

CMD ["python3", "main.py"]
