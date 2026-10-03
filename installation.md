**Install pyenv**

Run the following command to install pyenv:

```bash
curl https://pyenv.run | bash
```
pyenv allows you to install and manage multiple Python versions on the same system.

__Configure pyenv__
Add the following configuration to your ~/.bashrc file:

```bash
echo 'export PATH="$HOME/.pyenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
```
After adding the configuration, reload your shell:

```bash
source ~/.bashrc
```

__Verify the Installation__
Run the following command to verify that pyenv was installed successfully:

```bash
pyenv --version
```

<img width="368" height="113" alt="image" src="https://github.com/user-attachments/assets/58944c2a-e168-41ef-ab51-3a80a64ae358" />

