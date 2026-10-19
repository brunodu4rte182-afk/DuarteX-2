# DuartX Solutions

Landing page institucional B2B para apresentar os serviços de Inteligência de Dados, Automação de Processos e CRM da DuartX Solutions. O site é responsivo, mobile-first e direciona conversas comerciais para o WhatsApp.

## Visão geral

A página reúne uma apresentação do negócio, mockup ilustrativo de integrações, comparativo operacional, catálogo de soluções, processo de trabalho, benefícios, perguntas frequentes, chamada para contato, experiência visual Spline, relatos demonstrativos e rodapé com Instagram.

O mockup do dashboard é uma **simulação visual**: o valor de receita e o traçado do gráfico se atualizam periodicamente para dar sensação de movimento, mas não leem dados reais da empresa nem estão conectados a um CRM, ERP ou ferramenta de BI. A atualização é desativada quando o navegador indica `prefers-reduced-motion`.

Os relatos e avaliações apresentados na página são conteúdo demonstrativo e estão sinalizados na seção. Antes de usá-los como depoimentos comerciais, substitua-os por testemunhos reais e autorizados.

## Tecnologias

- **React 19** — composição da interface em componentes.
- **TypeScript 5.9** — tipagem do cliente e verificações estáticas.
- **Vite 7** — servidor de desenvolvimento e build estático.
- **Wouter** — roteamento leve para a página principal e fallback 404.
- **Framer Motion** — transições e movimentos de interface, respeitando preferências de movimento reduzido.
- **Lucide React** — ícones da interface.
- **CSS responsivo** — design system próprio em `client/src/index.css`, com gradientes, estados de foco e breakpoints mobile-first.
- **Tailwind CSS 4** — plugin disponível no toolchain do Vite; a maior parte do visual desta landing page é composta por regras CSS próprias.
- **pnpm 10.18** — gerenciador de pacotes declarado no projeto.

O repositório também contém dependências e módulos do template inicial (incluindo Express, tRPC e Drizzle). A implantação atual deste site está configurada como **estática**, sem servidor de aplicação ou banco de dados habilitado.

## Estrutura principal

```text
client/
├── index.html                 # Documento HTML e metadados
├── public/
│   ├── favicon.svg             # Símbolo da marca
│   └── manus-routes.json       # Manifesto de rotas do host
└── src/
    ├── App.tsx                 # Tema, limites de erro e rotas
    ├── main.tsx                # Inicialização React
    ├── index.css               # Estilos e responsividade
    ├── site-config.ts          # WhatsApp, Instagram e URL da cena Spline
    ├── pages/
    │   ├── Home.tsx             # Seções e interações da landing page
    │   └── NotFound.tsx         # Fallback 404
    ├── components/             # Componentes reutilizáveis do template
    ├── contexts/               # Contextos React, incluindo tema
    └── lib/                    # Utilitários e clientes do template

server/                         # Scaffold de servidor do template; não usado pelo build estático atual
```

## Configurações públicas do site

Edite `client/src/site-config.ts` para ajustar os destinos e mensagens visíveis no site:

- `whatsappPhone`: número internacional, somente dígitos. Está vazio por padrão; informe o número oficial antes de divulgar o CTA.
- `whatsappMessage`: mensagem pré-preenchida do botão de WhatsApp.
- `instagramUrl`: perfil oficial `https://www.instagram.com/duartx.solutions/`.
- `splineSceneUrl`: URL pública da cena que alimenta a área Spline.

Não coloque tokens, senhas ou credenciais nessa configuração do cliente. Tudo que estiver nela será enviado ao navegador.

## Desenvolvimento local

Requisitos: Node.js compatível com o Vite 7 e pnpm 10.18.

```bash
pnpm install --frozen-lockfile
pnpm dev:static
```

O servidor Vite escuta a porta `3000` por padrão e aceita a variável `PORT` para definir outra porta disponível.

## Verificações e build

```bash
pnpm check          # TypeScript, sem gerar arquivos
pnpm test           # Suíte Vitest declarada no package.json
pnpm build:static   # Build de produção para o site estático
```

O build estático é gravado em `dist/public/`. Para publicação estática em um host como Vercel, use `pnpm build:static` como comando de build e `dist/public` como diretório de saída. A integração do repositório e a configuração do domínio devem ser feitas na conta de hospedagem; os registros DNS necessários dependem do domínio e das instruções fornecidas pelo provedor.

O projeto também mantém os scripts `pnpm build` e `pnpm start` para o scaffold de servidor do template; eles não fazem parte do fluxo estático atualmente selecionado.

## Licença

O `package.json` declara a licença MIT. Verifique direitos de marca, conteúdo, cenas, fontes e ativos de terceiros antes de redistribuir o projeto.
