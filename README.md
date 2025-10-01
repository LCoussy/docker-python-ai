# 🚀 Docker Python AI

Docker container pour **Deep/Machine Learning en Python**, incluant la plupart des bibliothèques nécessaires : TensorFlow, PyTorch, Keras, MXNet, Scikit-Learn, Pandas, Jupyter Notebook, et bien d’autres.

---

## 🔧 Contenu de l’image

* **Base** : `debian:bullseye-slim`
* **Python** : 3.13.7 (compilé depuis les sources, optimisé)
* **Librairies scientifiques** : NumPy, Pandas, SciPy, Scikit-learn, Matplotlib, Seaborn
* **Deep Learning** : TensorFlow, Keras, PyTorch, MXNet, XGBoost
* **Outils pratiques** : Jupyter Notebook (préconfiguré sans token), Graphviz, yfinance
* **Optimisations** : nettoyage après build pour réduire la taille de l’image

---

## 📦 Construction de l’image

Clone le repo (ou copie le Dockerfile), puis exécute :

```bash
docker build -t deep-learning .
```

ou exécute : 

```bash
docker pull lcoussy/docker-python-ai
```

---

## ▶️ Lancer le container

### 1. Sans GPU (CPU uniquement)

Lancer dans le répertoire avec les notebooks :

```bash
docker run -it --rm --name docker-ai \
    -p 8888:8888 \
    -v $(pwd):/home/notebooks \
    lcoussy/docker-python-ai
```

➡️ Ensuite, ouvre ton navigateur sur [http://localhost:8888](http://localhost:8888).

---

### 2. Avec GPU (via NVIDIA Docker)

Assure-toi d’avoir installé :

* Les **drivers NVIDIA** sur ta machine
* Le **runtime nvidia-container-toolkit** ([doc officielle](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html))

Puis lance dans le répertoire avec les notebooks :

```bash
docker run -it --rm --name docker-ai \
    --gpus all \
    -p 8888:8888 \
    -v $(pwd):/home/notebooks \
    lcoussy/docker-python-ai
```

Cela permettra à TensorFlow, PyTorch, et MXNet de détecter et utiliser ton GPU.

---

## ⚡ Tips

* Pour personnaliser la liste des bibliothèques installées, modifie `PIP_PACKAGES` dans le Dockerfile.

---

## 🌐 Ressources

* Fork de cette image : [Docker Hub – petronetto/docker-python-deep-learning](https://hub.docker.com/r/petronetto/docker-python-deep-learning)
