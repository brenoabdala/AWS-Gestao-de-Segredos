<h2>Guia de Implementação: AWS KMS e Secrets Manager</h2>

<p>Abaixo, detalho o procedimento técnico realizado para a configuração da camada de segurança de dados sensíveis:</p>

<h3>1. Criação da Chave de Criptografia (AWS KMS)</h3>
<p>O KMS fornece a infraestrutura para gerar e gerenciar as chaves que protegem os dados.</p>
<ul>
    <li>No console AWS, acesse <b>Key Management Service (KMS)</b>.</li>
    <li>Selecione <b>Chaves geradas pelo cliente</b> e clique em <b>Criar chave</b>.</li>
    <li><b>Tipo de chave:</b> Escolha <b>Simétrica</b>.</li>
    <li><b>Uso da chave:</b> Marque <b>Criptografar e descriptografar</b>.</li>
    <li><b>Alias:</b> Defina o nome de identificação (ex: <code>chave-estudo-alura-bq</code>).</li>
    <li>Nas telas de permissões, selecione o seu usuário como administrador e como usuário da chave para garantir controle total.</li>
</ul>



<h3>2. Armazenamento de Credenciais (AWS Secrets Manager)</h3>
<p>O Secrets Manager utiliza a chave KMS para selar informações como senhas e usuários.</p>
<ul>
    <li>No console, acesse <b>Secrets Manager</b> e clique em <b>Armazenar um novo segredo</b>.</li>
    <li>Escolha o tipo <b>Outro tipo de segredo</b> para chaves personalizadas.</li>
    <li>Em <b>Pares de chave/valor</b>, insira os dados (ex: Chave: <code>USUARIO</code> / Valor: <code>seu_usuario</code>).</li>
    <li><b>Criptografia:</b> Selecione na lista a chave KMS criada no passo anterior (<code>chave-estudo-alura-bq</code>).</li>
    <li>Defina um nome para o segredo (ex: <code>projeto/banco/credenciais</code>).</li>
    <li>Na tela de rotação, mantenha <b>Desativado</b> para evitar custos adicionais em ambiente de estudo.</li>
</ul>



<hr>
