# Usa a imagem mais recente do Arch Linux
FROM archlinux:latest

# Define variáveis para o usuário e diretório de trabalho
ENV USERNAME=leonel
ENV HOME=/home/$USERNAME

# Atualiza o sistema e instala pacotes essenciais
RUN pacman -Syu --noconfirm \
    sudo \
    git \
    vim \
    base-devel \
    && pacman -Scc --noconfirm  # Limpa o cache do pacman

# Cria o usuário leonel e adiciona ao grupo sudo
RUN useradd -m -G wheel -s /bin/bash $USERNAME \
    && echo "$USERNAME ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Define o usuário padrão para evitar rodar como root
USER $USERNAME
WORKDIR $HOME

# Comando padrão ao iniciar o container
CMD ["/bin/bash"]
