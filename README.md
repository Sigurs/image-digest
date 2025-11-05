#  image-digest
The purpose of this project is to take an input of yaml file(s) and then output all the images, tags and fetches their sha256 digests.  
Depends on curl, jq and yq (kislyuk variant).  
One huge requirement for me was to keep this easily transferable, thus a bash script.  

Notable features: 
 - Uses `$HOME/.docker/config.json` as credential sources when needed.  
 - Defaults to latest if no tag is given.  
 - Supports different architectures with --arch.

Usage:  
```
# Input, option 1
helm template . | image-digest -f -
# Input, option 2
image-digest -f yamls/
# Input, option 3
image-digest -f file.yaml
# Input, option 4
image-digest ubuntu:25.10

# Output
registry-1.docker.io/library/ubuntu:25.10@sha256:9b61739164b58f2263067bd3ab31c7746ded4cade1f9d708e6f1b047b408a470
registry-1.docker.io/library/nging:latest@sha256:f547e3d0d5d02f7009737b284abc87d808e4252b42dceea361811e9fc606287f
quay.io/keycloak/keycloak:26.4.2@sha256:d06f9d34c61721b62b585d08ebf85b1b62e28c68895af6c3a374908e37c9e085
ghcr.io/home-assistant/home-assistant:2025.10.4@sha256:3778096a89fbd085cbf8fd0bc168d8a4391a3f3268b287b31ecd38af2001d225
```

Options:
```
-f, --file      input file ( '-' for stdin)
-a, --arch      architecture (defaults to amd64)
```