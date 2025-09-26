### Docker

Docker is a platform that allows developers to package applications and all their dependencies into something called a container, so they can run anywhere, consistently.

Docker lets you create a "box" (container) that holds your app, along with everything it needs — so it runs the same on your computer, a server, or in the cloud.

**Why Do We Need Docker?**

Without Docker:
- An app might work on your machine but not on someone else’s
- You need to install the right Python/Java/Node version, libraries, tools, configs — manually

With Docker:
- Your package everything together
- Your app runs identically everywhere

### What is a Container?

A container is a lightweight, standalone environment where your app runs.

Think of it as a mini-computer inside your real computer:
- Has its own file system
- Its own libraries
- Runs your app in isolation

But unlike a virtual machine, containers:
- Are much faster
- Use less memory
- Start in seconds

### How Docker Works (Simplified)

1. You create a Dockerfile that tells Docker how to build your app environment.
```
FROM python:3.9
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["python", "app.py"]
```

2. Build the image (a snapshot of the app):
```
docker build -t my-app .
```

3. Run a container from that image:
```
docker run -p 5000:5000 my-app
```

Now your app is running in its own portable box!