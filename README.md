[GitHub](https://github.com/nephatrine/docker-h5ai) |
[DockerHub](https://hub.docker.com/r/nephatrine/h5ai/) |
[unRAID](https://github.com/nephatrine/unraid-docker-templates)

# H5AI Docker

This docker runs the [H5AI](https://larsjung.de/h5ai/) web directory index. Just put files and
folders into the volume mapped to `/mnt/media` and they will be made accessible through the web
interface. For private files, you can either lock them down via the NGINX config (there's an
example that will hide files under /local/) or use a separate docker that is not publicly
accessible in the first place.

Certbot (LetsEncrypt) is installed to handle obtaining SSL certs in case this is your only web
docker. If you plan on hosting multiple applications/dockers, though I suggest having one
[nginx-ssl](https://hub.docker.com/r/nephatrine/nginx-ssl/) docker that is publicly visible and
handles the SSL certs for all domains. That docker can then proxy all your other nginx dockers
which would actually be running on non-public IPs under plain HTTP.

## Settings

- **DNSADDR:** DNS IPs (space-delimited)
- **PUID:** Volume Owner UID
- **PGID:** Volume Owner GID
- **SSLEMAIL:** LetsEncrypt Email Address
- **SSLDOMAINS:** LetsEncrypt (Sub)domains (comma-delimited)
- **TZ:** Time Zone

## Mount Points

- **/mnt/config:** Configuration Volume
- **/mnt/media:** Files/Data Volume