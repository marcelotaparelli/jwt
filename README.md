# jwt

## Algoritmo de Login com JWT em Node.js

- **1. Usuário envia credenciais**  
  - O cliente (navegador ou app) manda **email/usuário e senha** para o servidor via uma requisição HTTP (geralmente POST).

<br><br>

- **2. Servidor valida credenciais**  
  - O servidor compara os dados recebidos com os armazenados no banco de dados.  
  - Se a senha estiver correta, o usuário é considerado autenticado.

<br><br>

- **3. Criação do Payload do JWT**  
  - O servidor monta um objeto com informações relevantes do usuário (ex.: `id`, `nome`, `role`).  
  - Esse objeto é chamado de **payload** e será embutido no token.

<br><br>

- **4. Definição do Header do JWT**  
  - O servidor define o cabeçalho do token, especificando o algoritmo de assinatura (ex.: HS256).  
  - O header indica como o token será protegido.

<br><br>

- **5. Assinatura do Token**  
  - O servidor junta o **header + payload** e aplica uma função criptográfica (ex.: HMAC-SHA256) usando uma **chave secreta**.  
  - Isso gera a **signature**, que garante que o token não foi adulterado.

<br><br>

- **6. Envio do Token ao Cliente**  
  - O servidor devolve o JWT completo (`header.payload.signature`) ao cliente.  
  - O cliente guarda esse token (normalmente em localStorage ou cookies).

<br><br>

- **7. Uso do Token em Requisições Futuras**  
  - Cada vez que o cliente faz uma requisição protegida (ex.: acessar perfil, consultar dados), ele envia o token no **header Authorization** da requisição (`Bearer <token>`).

<br><br>

- **8. Validação do Token no Servidor**  
  - O servidor recebe o token e verifica:  
    - Se a assinatura é válida (não foi alterada).  
    - Se o token não expirou.  
  - Se tudo estiver correto, o servidor libera o acesso ao recurso solicitado.

<br><br>

- **9. Resposta ao Cliente**  
  - O servidor retorna os dados solicitados.  
  - Caso o token seja inválido ou expirado, retorna um erro (ex.: 401 Unauthorized).
