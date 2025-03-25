# How to Keep Python Projects Clean with Virtual Environments & Dependencies

## 1️⃣ Use a Virtual Environment 🛠️
Keeps dependencies isolated:

```
python3 -m venv venv  
source venv/bin/activate  # Mac/Linux  
venv\Scripts\activate     # Windows  
```

Deactivate with `deactivate`.

## 2️⃣ Manage Dependencies Properly 📌

Save installed packages:

```
pip freeze > requirements.txt  
```

Install from file:

```
pip install -r requirements.txt  
```

## 3️⃣ Better Dependency Management with pip-tools 🚀

```
pip install pip-tools  
pip-compile        # Generates a pinned requirements.txt  
pip-sync           # Installs exactly what's in requirements.txt  
```

## 4️⃣ Install Specific Package Versions 📉📈

```
pip install "numpy<2"       # Install specific version  
pip install --upgrade numpy  # Upgrade package  
pip uninstall numpy         # Remove package  
```
