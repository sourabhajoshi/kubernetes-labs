### Kubernetes

Kubernetes (also called K8s) is a tool that manages containers.

If Docker helps you run a single container, Kubernetes helps you run many containers across many machines, and keep them organized, available, and scalable.

Imagine you run a pizza shop:

- One oven (Docker) can bake pizzas (your app).
- But if you have 100 customers, one oven isn't enough.
- You now need many ovens, workers, delivery, and a manager to:
    - Assign tasks
    - Replace broken ovens
    - Scale up/down based on orders
    - Make sure no one goes hungry

Kubernetes is that manager.

It:
- Keeps your app running
- Handles more customers (traffic)
- Fixes problems automatically
- Scales the app up or down

### Kubernetes + Docker

- Docker: runs one container
- Kubernetes: runs lots of containers across many computers

They work together:
- You build your app with Docker
- You run & manage it at scale with Kubernetes