<h1>Infraestrutura de Segurança e Gestão de Segredos na AWS</h1>

<h2>Objetivo</h2>
<p> O projeto tem como objetivo estabelecer uma arquitetura segura para o armazenamento de dados sensíveis. </p>

<h2>Arquitetura de Segurança</h2>
<p>
  A solução baseia-se na separação de responsabilidades, utilizando dois serviços principais que trabalham de forma integrada:
</p>

<table width="100%">
  <thead>
    <tr>
      <th align="left">Serviço</th>
      <th align="left">Papel na Arquitetura</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>AWS KMS</b></td>
      <td>Responsável pela geração e controle da chave mestra (CMK). É o motor de criptografia.</td>
    </tr>
    <tr>
      <td><b>AWS Secrets Manager</b></td>
      <td>Funciona como o cofre lógico que armazena pares de chave/valor (usuários e senhas).</td>
    </tr>
  </tbody>
</table>

<h2>Passo a Passo da Implementação</h2>

<h3>Provisionamento da Chave Mestra (KMS)</h3>
<p>
  Iniciei criando uma chave simétrica personalizada com o alias <code>chave-estudo-alura-bq</code>. A escolha por uma chave gerenciada pelo cliente (Customer Managed Key) permite um controle granular sobre quem pode rotacionar ou deletar a chave, além de fornecer logs de auditoria detalhados.
</p>

<h3>Configuração do Cofre (Secrets Manager)</h3>
<p>
  Com a chave KMS ativa, configurei o segredo para um banco de dados fictício. No processo:
</p>
<ul>
  <li>Defini pares de chave/valor para <code>USUARIO</code> e <code>SENHA</code>.</li>
  <li><b>Ponto Crítico:</b> Vinculei explicitamente o segredo à chave <code>chave-estudo-alura-bq</code>, garantindo que o segredo só possa ser lido por quem possuir permissão na chave específica.</li>
</ul>

<h2>Visão Multi-Cloud (AWS vs Azure)</h2>
<p>
  Para fins de portfólio e clareza técnica entre plataformas, esta implementação segue o mesmo raciocínio do <b>Azure Key Vault</b>, onde o KMS equivale às <i>Keys</i> e o Secrets Manager equivale aos <i>Secrets</i>.
</p>
