In the following instructions, both Azure CLI and MSAL have a work-in-progress branch named `mi`.

You may install the dev code and test if it works as expected (on Debian/Ubuntu):

```
sudo apt install python3 python3-venv
mkdir mi
cd mi
git clone https://github.com/jiasli/azure-cli --branch mi --depth 1
git clone https://github.com/AzureAD/microsoft-authentication-library-for-python --branch mi --depth 1
python3 -m venv env
. env/bin/activate
pip install azdev
pip install -e microsoft-authentication-library-for-python[broker]
azdev setup -c
az --login
```

RPM-based systems are similar, you only need to switch apt to dnf. As for Windows, you will need to manually download and install python and git, and change the `bin` folder in the above step to `Scripts`.
