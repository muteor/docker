FROM buoyantio/debian-32-bit

MAINTAINER Keith Pope <thepope@thepopeisdead.com>

# Get exec binary
RUN mkdir /linkerd
ADD https://github.com/BuoyantIO/linkerd/releases/download/0.7.4/linkerd-0.7.4-exec /linkerd/
RUN chmod +x /linkerd/linkerd-0.7.4-exec

# linkerd | admin
EXPOSE 4140 9990

# set env vars copied from offical container
ENV HOME /linkerd
ENV EXEC /linkerd/linkerd-0.7.4-exec
