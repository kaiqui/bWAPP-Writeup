Aqui está um write-up em formato Markdown descrevendo como explorar a vulnerabilidade "Broken Auth. - Insecure Login Forms" nos níveis low e medium no bWAPP:

---

# bWAPP - A2: Broken Authentication & Session Management

## Vulnerabilidade: Broken Auth. - Insecure Login Forms

Este write-up detalha a exploração da vulnerabilidade "Broken Authentication - Insecure Login Forms" nos níveis low e medium do bWAPP.

### Nível Low

#### Exploração

- **Passo 1**: Acesse a página de login do bWAPP.
- **Passo 2**: Visualize o código-fonte da página web.
- **Passo 3**: No código-fonte, procure pelas credenciais expostas. Para este nível, as credenciais são:
  - **Username**: `tonystark`
  - **Password**: `I am Iron Man`
- **Passo 4**: Insira as credenciais encontradas no formulário de login e acesse o sistema.

### Nível Medium

#### Exploração

- **Passo 1**: Acesse a página de login do bWAPP.
- **Passo 2**: Visualize o código-fonte da página web.
- **Passo 3**: No código-fonte, localize o username `brucebanner`.
- **Passo 4**: A senha está escondida e é validada pela função JavaScript `unlock_secret()`.
- **Passo 5**: Modifique a função `unlock_secret()` para exibir a senha no console:
  
  ```javascript
    function unlock_secret()
    {

        var bWAPP = "bash update killed my shells!"

        var a = bWAPP.charAt(0);  var d = bWAPP.charAt(3);  var r = bWAPP.charAt(16);
        var b = bWAPP.charAt(1);  var e = bWAPP.charAt(4);  var j = bWAPP.charAt(9);
        var c = bWAPP.charAt(2);  var f = bWAPP.charAt(5);  var g = bWAPP.charAt(4);
        var j = bWAPP.charAt(9);  var h = bWAPP.charAt(6);  var l = bWAPP.charAt(11);
        var g = bWAPP.charAt(4);  var i = bWAPP.charAt(7);  var x = bWAPP.charAt(4);
        var l = bWAPP.charAt(11); var p = bWAPP.charAt(23); var m = bWAPP.charAt(4);
        var s = bWAPP.charAt(17); var k = bWAPP.charAt(10); var d = bWAPP.charAt(23);
        var t = bWAPP.charAt(2);  var n = bWAPP.charAt(12); var e = bWAPP.charAt(4);
        var a = bWAPP.charAt(1);  var o = bWAPP.charAt(13); var f = bWAPP.charAt(5);
        var b = bWAPP.charAt(1);  var q = bWAPP.charAt(15); var h = bWAPP.charAt(9);
        var c = bWAPP.charAt(2);  var h = bWAPP.charAt(2);  var i = bWAPP.charAt(7);
        var j = bWAPP.charAt(5);  var i = bWAPP.charAt(7);  var y = bWAPP.charAt(22);
        var g = bWAPP.charAt(1);  var p = bWAPP.charAt(4);  var p = bWAPP.charAt(28);
        var l = bWAPP.charAt(11); var k = bWAPP.charAt(14);
        var q = bWAPP.charAt(12); var n = bWAPP.charAt(12);
        var m = bWAPP.charAt(4);  var o = bWAPP.charAt(19);

        var secret = (d + "" + j + "" + k + "" + q + "" + x + "" + t + "" +o + "" + g + "" + h + "" + d + "" + p);

        console.log(secret)

    }

    unlock_secret()
  ```

- **Passo 6**: Execute a função modificada. A saída será a senha: `"hulk smash!"`.
- **Passo 7**: Use o username `brucebanner` e a senha `hulk smash!` para fazer login no sistema.

### Conclusão

A exploração dessas vulnerabilidades demonstra a importância de não deixar credenciais expostas no código-fonte e de proteger adequadamente as funções de autenticação e validação de senha. Em ambientes reais, tais práticas podem levar a sérias brechas de segurança.

