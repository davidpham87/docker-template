ARG IMAGE

FROM babashka/babashka as bb

FROM $IMAGE

USER root

COPY --from=bb /usr/local/bin/bb /usr/local/bin/bb

# should be nearly always overridden during `docker build` with YOUR user id via `--build-arg USER_ID=$(id -u) --build-arg GROUP_ID=$(id -g)` or similar

ARG USER_ID=999
ARG GROUP_ID=999
ARG USERNAME=user

RUN addgroup --gid $GROUP_ID $USERNAME || true
RUN adduser --disabled-password --gecos '' --uid $USER_ID --gid $GROUP_ID $USERNAME || usermod -l $USERNAME $(id -nu $USER_ID)
RUN usermod -aG sudo $USERNAME || true
RUN usermod -d /home/$USERNAME -m $USERNAME

RUN chown -R $USERNAME:$USERNAME /tmp/.m2/repository

USER $USERNAME
WORKDIR /home/$USERNAME

RUN cp /usr/local/bin/APserver /home/$USERNAME || true

# RUN apt-get install ....
# RUN pip3 install ....
# RUN Rscript -e 'install.packages("....",repo="http://cran.rstudio.com/")'
