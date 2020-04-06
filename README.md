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

## Roadmap

See the [Issues](https://github.com/flathub/org.onionshare.OnionShare/issues/) tracker.