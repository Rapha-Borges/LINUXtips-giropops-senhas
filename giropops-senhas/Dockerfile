FROM cgr.dev/chainguard/python:latest-dev@sha256:be487ac35cb06641a8aca030ac547d7fe754b608d95d895e56ef34917c9f8949 as builder
WORKDIR /app
COPY . /app
RUN pip install -r requirements.txt --user

FROM cgr.dev/chainguard/python:latest@sha256:5f16431f56f330925a9c8f5168b31ca65f603de15b127b376f8532bab11583c0
WORKDIR /app
COPY --from=builder /home/nonroot/.local/lib/python3.12/site-packages /home/nonroot/.local/lib/python3.12/site-packages
COPY --from=builder /app /app

ENTRYPOINT ["python", "-m", "flask", "run", "--host=0.0.0.0"]