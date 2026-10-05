## JupyterLab Setup

After creating the virtual environment, activate it:

```bash
source .venv/bin/activate
```

Install JupyterLab:

```bash
pip install jupyterlab
```

Start JupyterLab:

```bash
jupyter lab
```

JupyterLab will normally be available at:

```text
http://localhost:8888
```

You can open this URL in your browser.

---

## Issue Faced: `_sqlite3` Error

While running JupyterLab, I faced:

```text
ModuleNotFoundError: No module named '_sqlite3'
```
<img width="680" height="396" alt="image" src="https://github.com/user-attachments/assets/d2da9db9-043e-487a-88d8-56fb23d14ef5" />


This happened because Python was installed using `pyenv`, and the Python installation did not have SQLite support.

The Python installation was:

```text
/home/pbansod/.pyenv/versions/3.12.15/
```

### Fix

First, install the SQLite development package:

```bash
sudo apt update
```

```bash
sudo apt install libsqlite3-dev
```

Install the common Python build dependencies as well:

```bash
sudo apt install build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libncursesw5-dev libffi-dev liblzma-dev tk-dev libsqlite3-dev
```

Since Python was installed through `pyenv`, uninstall the existing Python version:

```bash
pyenv uninstall 3.12.15
```

Install it again:

```bash
pyenv install 3.12.15
```

Verify that SQLite support is available:

```bash
python -c "import sqlite3; print(sqlite3.sqlite_version)"
```

If a SQLite version is displayed, the issue is fixed.

---

## Recreate the Virtual Environment

Because the existing virtual environment was created using the previous Python installation, remove it:

```bash
cd ~/practice-python
```

```bash
rm -rf .venv
```

Create a new virtual environment:

```bash
python -m venv .venv
```

Activate it:

```bash
source .venv/bin/activate
```

Install the project dependencies:

```bash
pip install -r requirements.txt
```

If JupyterLab is not included in `requirements.txt`, install it:

```bash
pip install jupyterlab
```

Finally, start JupyterLab:

```bash
jupyter lab
```

Open:

```text
http://localhost:8888
```

### Complete Command Flow

```bash
sudo apt update
sudo apt install libsqlite3-dev
sudo apt install build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libncursesw5-dev libffi-dev liblzma-dev tk-dev libsqlite3-dev

pyenv uninstall 3.12.15
pyenv install 3.12.15

python -c "import sqlite3; print(sqlite3.sqlite_version)"

cd ~/practice-python
rm -rf .venv
python -m venv .venv
source .venv/bin/activate

pip install -r requirements.txt
pip install jupyterlab

jupyter lab
```

JupyterLab should then be accessible at:

```text
http://localhost:8888
```
<img width="690" height="398" alt="image" src="https://github.com/user-attachments/assets/901ecfb5-cbeb-4e4b-bfb2-82a8cb3ed955" />

