# FROM phusion/baseimage
# FROM debian:jessie

# RUN apt-get update
# RUN apt-get install -y openssh-server

# EXPOSE 22
# CMD ["/usr/bin/sshd", "-D"]

# FROM ubuntu:14.04

# RUN /bin/sh -c "while true; do echo hello world; sleep 1; done"
# RUN /bin/sh -c "echo hello world"

# Use phusion/baseimage as base image. To make your builds
# reproducible, make sure you lock down to a specific version, not
# to `latest`! See
# https://github.com/phusion/baseimage-docker/blob/master/Changelog.md
# for a list of version numbers.

FROM phusion/baseimage:latest

# Set correct environment variables.
ENV HOME /root

# Regenerate SSH host keys. baseimage-docker does not contain any, so you
# have to do that yourself. You may also comment out this instruction; the
# init system will auto-generate one during boot.
RUN /etc/my_init.d/00_regen_ssh_host_keys.sh

# Use baseimage-docker's init system.
CMD ["/sbin/my_init", "--enable-insecure-key"]

# ...put your own build instructions here...

# Clean up APT when done.
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
