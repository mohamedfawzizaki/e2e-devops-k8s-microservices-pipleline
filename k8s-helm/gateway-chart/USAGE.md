You can access your **Kubernetes Ingress** exposed services locally in **Minikube** like this:

---

## ✅ **1. Ensure Ingress Controller is Running**

Enable the NGINX ingress addon in Minikube:

```bash
minikube addons enable ingress
```

Check the ingress controller pod:

```bash
kubectl get pods -n kube-system -l app.kubernetes.io/name=ingress-nginx
```

---

## ✅ **2. Get the Ingress Controller’s IP**

For Minikube (Docker driver), the NGINX ingress controller is exposed **on Minikube's VM IP**, or can be accessed using a Minikube tunnel.

Run this to start a tunnel in a separate terminal:

```bash
minikube tunnel
```

Keep this terminal open.

---

## ✅ **3. Check the Ingress Resource**

Run:

```bash
kubectl get ingress
```

Example output:

```
NAME              CLASS    HOSTS                     ADDRESS         PORTS   AGE
gateway-ingress   nginx    reactjs.local,api.local   192.168.49.2    80      2m
```

Take note of the **ADDRESS** column (`192.168.49.2` or similar).

---

## ✅ **4. Update Your `/etc/hosts` (Linux/macOS) or `C:\Windows\System32\drivers\etc\hosts` (Windows)**

Add an entry like this (replace with your Minikube IP):

```
192.168.49.2 reactjs.local
192.168.49.2 api.local
```

If using the `minikube tunnel`, it may be `127.0.0.1`:

```
127.0.0.1 reactjs.local
127.0.0.1 api.local
```

---

## ✅ **5. Access in Browser**

* ReactJS App: [http://reactjs.local/](http://reactjs.local/)
* Backend API: [http://api.local/](http://api.local/)

---

## ❗ If using a browser and it fails:

* Try using `curl` first:

```bash
curl -v http://reactjs.local/
curl -v http://api.local/
```

---

## 🔧 **Alternative (Without /etc/hosts)**

If you don’t want to edit `/etc/hosts`, you can access the ingress by Minikube IP:

```bash
curl -H "Host: reactjs.local" http://192.168.49.2/
curl -H "Host: api.local" http://192.168.49.2/
```

But the **browser requires /etc/hosts**, unless you use a local DNS tool.

---
