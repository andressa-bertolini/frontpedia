incompatibilidade entre a versão do Node.js e as bibliotecas de criptografia que ele está tentando usar

- Verifique a versão do Node instalada com o comando `node -v`. Recomendo atualizar para uma versão LTS mais recente (como a 18 ou 20).
- Tente iniciar o seu projeto com o seguinte comando:
export NODE_OPTIONS=--openssl-legacy-provider
npm start