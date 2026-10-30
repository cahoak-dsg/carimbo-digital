# Carimbo Digital v15 - GitHub + Netlify

Esta v15 esta configurada para o projeto Supabase NOVO informado em 29/10/2026.
O `index.html` contem somente a URL e a **chave publicavel** do Supabase. Nao contem senha nem o e-mail pessoal do responsavel.

## Supabase ja configurado

- Banco inicial instalado: 5 tabelas, bucket `documentos` privado.
- Login criado em Authentication > Users.
- Perfil `adm-itauba`, `role=financeiro`, `acesso_total=true`.
- Projeto utilizado pelo HTML: `https://pxsaphnwbfkhesuaqbbp.supabase.co`.

## Login compartilhado sem publicar e-mail no GitHub

A Supabase Auth exige um e-mail para login por senha. Para preservar o e-mail pessoal, o apelido `adm-itauba` e habilitado automaticamente **por navegador**:

1. Na primeira vez em CADA notebook ou navegador, entre com o e-mail cadastrado no Supabase e a senha.
2. Apos entrar com sucesso, o navegador grava apenas a correspondencia do apelido com o e-mail (nao a senha).
3. Nos proximos logins **no mesmo navegador**, pode usar `adm-itauba` e a senha.
4. O checkbox "Permanecer conectado" controla a persistencia da sessao.

**Privacidade:** o e-mail fica no armazenamento local daquele navegador e pode ser encontrado por quem tem acesso a ele. Nao fica no codigo publicado no GitHub. Para o piloto com notas reais, prefira no futuro um e-mail compartilhado exclusivamente corporativo.

## GitHub + Netlify

1. Crie um repositorio **privado** `carimbo-digital` no GitHub.
2. Extraia o ZIP e envie **index.html**, **netlify.toml** e **README.md** para a raiz do repositorio, branch `main`. Nao envie o ZIP fechado.
3. No Netlify, conecte esse repositorio via **Add new project > Import an existing project > GitHub**.
4. Configuracao: branch `main`; build command **em branco**; publish directory `.`. O `netlify.toml` informa a pasta a publicar.
5. Publique e teste login e fluxo com PDF de teste.
6. Cada commit novo no `main` sera publicado automaticamente pelo Netlify.

Se quiser manter o endereco do site atual, em vez de criar um novo site no Netlify, conecte o repositorio ao projeto atual por **Project configuration > Developer settings > Continuous deployment > Repository > Link repository**.

## Seguranca e limites

- Nunca envie para GitHub senhas, `sb_secret_...`, `service_role` ou a senha do banco.
- A chave `sb_publishable_...` pode aparecer no HTML; a RLS do banco deve continuar ativa.
- Os quatro responsaveis usam uma identidade compartilhada: os registros nao individualizam quem realizou a acao.
- Uma imagem de assinatura nao substitui uma assinatura digital autenticada.
- O deploy do site pelo GitHub **nao executa migracoes SQL** no Supabase automaticamente.
- A integracao ao vivo no seu Supabase ainda precisa de teste manual.
