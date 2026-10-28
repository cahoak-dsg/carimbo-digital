# CARIMBO DIGITAL v14b — Supabase

Esta versão foi conectada ao projeto Supabase da empresa.

## O que mudou

- Login por e-mail e senha via Supabase Auth.
- O setor do usuário vem da tabela `profiles`.
- A fila é carregada da tabela `documents`.
- PDFs são armazenados no bucket privado `documentos`.
- Cada etapa cria uma linha em `document_versions` e em `document_history`.
- Financeiro cria o documento e envia para `aguardando_atesto`.
- Administração envia para `aguardando_diretoria`.
- Diretoria conclui e o documento aparece em `Concluídos`.

## Configuração embutida

O arquivo `index.html` contém apenas o Project URL e a Publishable Key do Supabase. A Publishable Key é própria para uso no navegador e não substitui as regras RLS. Nenhuma Secret Key ou `service_role` foi incluída.

## Antes de uso real

Testar todo o fluxo com documentos fictícios e revisar as regras de permissão antes de usar documentos confidenciais.
