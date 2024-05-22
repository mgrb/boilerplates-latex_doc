FROM ubuntu:22.04

# Avoid warnings by switching to noninteractive
ENV DEBIAN_FRONTEND=noninteractive

# Configure apt and install packages
RUN apt-get update -y && \
    apt-get upgrade -y && \
    apt-get install -y \
    curl \
    zsh \ 
    git 

# Install Starship prompt
RUN sh -c "$(curl -sS https://starship.rs/install.sh)" -y -f

WORKDIR /tmp

# Install TeXLive
RUN curl -L -o install-tl-unx.tar.gz https://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz && \
    zcat < install-tl-unx.tar.gz | tar xf - && \
    cd install-tl-* && \
    echo "selected_scheme scheme-basic" > texlive.profile && \
    echo "TEXDIR /usr/local/texlive" >> texlive.profile && \
    echo "TEXMFCONFIG ~/.texlive/texmf-config" >> texlive.profile && \
    echo "TEXMFHOME ~/texmf" >> texlive.profile && \
    echo "TEXMFLOCAL /usr/local/texlive/texmf-local" >> texlive.profile && \
    echo "TEXMFSYSCONFIG /usr/local/texlive/texmf-config" >> texlive.profile && \
    echo "TEXMFSYSVAR /usr/local/texlive/texmf-var" >> texlive.profile && \
    echo "TEXMFVAR ~/.texlive/texmf-var" >> texlive.profile && \
    echo "binary_x86_64-linux 1" >> texlive.profile && \
    echo "tlpdbopt_install_docfiles 0" >> texlive.profile && \
    echo "tlpdbopt_install_srcfiles 0" >> texlive.profile && \
    perl ./install-tl --profile=texlive.profile && \
    cd .. && \
    rm -rf install-tl-* 

ENV PATH="/usr/local/texlive/bin/x86_64-linux:${PATH}"

RUN tlmgr init-usertree && tlmgr update --self && tlmgr update --all

# Instale pacotes adicionais com tlmgr, incluindo pacotes de fontes e latexmk
RUN tlmgr install \
    libertine \
    inconsolata \
    latexmk \ 
    etoolbox \
    cite \
    caption \
    listings \
    xcolor 

RUN apt-get install -y texlive-lang-portuguese

# Clean up
RUN apt-get clean && \
    apt-get autoclean  && \
    rm -rf /var/lib/apt/lists/*

# Create a non-root user
RUN groupadd -r latex_grp && \
    useradd -m -g latex_grp -u 1001 -s /bin/zsh latex_usr

USER latex_usr


COPY .zshrc /home/latex_usr/

WORKDIR /latex_project

COPY ../ .

CMD ["tail", "-f", "/dev/null"]