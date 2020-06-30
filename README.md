# OnionShare
[OnionShare](https://onionshare.org/) is an open source tool that lets you securely and anonymously share a file of any
size.

## Build, Install and Run Flatpak (locally)

Assuming `flatpak`, `flatpak-builder`, and `git` packages are installed, run the following commands:

```sh
git clone https://github.com/flathub/org.onionshare.OnionShare.git
cd org.onionshare.OnionShare/
flatpak remote-add --if-not-exists --user flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak-builder build --force-clean --install-deps-from=flathub --install --user org.onionshare.OnionShare.json

# ...to run onionshare
flatpak run org.onionshare.OnionShare

# ...to uninstall the artifact
flatpak uninstall --delete-data --user org.onionshare.OnionShare

# ...and to clean-up everything
flatpak uninstall --unused --user
rm -rf .flatpak-builder/ build/
flatpak remote-delete --user flathub
```

## Making a new release

Build the latest poetry dependencies using [this script](https://github.com/flatpak/flatpak-builder-tools/tree/master/poetry).

```sh
# clone flatpak-build-tools
git clone https://github.com/flatpak/flatpak-builder-tools.git

# run the flatpak poetry generator
cd flatpak-builder-tools/poetry
./flatpak-poetry-generator.py ../../onionshare/poetry.lock

# find poetry deps in generated-poetry-sources.json
# (make sure to manually remove pyinstaller)
```

You must also manually add `setuptools` and `wheel`:

```
{
    "type": "file",
    "url": "https://files.pythonhosted.org/packages/e9/93/4860cebd5ad3ff2664ad3c966490ccb46e3b88458b2095145bca11727ca4/setuptools-47.3.1-py3-none-any.whl",
    "sha256": "4ba6f9789ea243a6b8ba57da81f75a53494456117810436fd9277a74d1c915d1"
},
{
    "type": "file",
    "url": "https://files.pythonhosted.org/packages/8c/23/848298cccf8e40f5bbb59009b32848a4c38f4e7f3364297ab3c3e2e2cd14/wheel-0.34.2-py2.py3-none-any.whl",
    "sha256": "df277cb51e61359aba502208d680f90c0493adec6f0e848af94948778aed386e"
}
```

## Roadmap

See the [Issues](https://github.com/flathub/org.onionshare.OnionShare/issues/) tracker.