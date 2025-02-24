FROM pihole/pihole:2025.02.5

# Set the OCI Image Specification source label to the Pihole repository to enable tools 
# like Renovate and Dependabot to automatically fetch release notes for new versions.
LABEL org.opencontainers.image.source="https://github.com/pi-hole/pi-hole"

RUN apt update && apt install -y unbound

COPY lighttpd-external.conf /etc/lighttpd/external.conf 
COPY unbound-pihole.conf /etc/unbound/unbound.conf.d/pi-hole.conf
COPY 99-edns.conf /etc/dnsmasq.d/99-edns.conf
RUN mkdir -p /etc/services.d/unbound
COPY unbound-run /etc/services.d/unbound/run

ENTRYPOINT ./s6-init