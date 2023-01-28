FROM python:3.10-slim

#update PATH
ENV PATH="/home/appuser/.local/bin:$PATH"
RUN echo $PATH

# create user
RUN adduser --disabled-password --gecos "" appuser
USER appuser

# set the working directory
WORKDIR /home/appuser

# install dependencies
COPY ./requirements.txt ./
RUN pip install --user --no-cache-dir --upgrade -r requirements.txt

# copy the src to the folder
COPY ./src ./src

# start the server
CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "80", "--reload"]
