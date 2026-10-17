# Barber Shop

Aplicação web para encontrar barbearias, consultar serviços e horários disponíveis e gerenciar reservas.

## Funcionalidades

- **Página inicial (`/`)**: exibe uma saudação, busca, categorias de serviços, reservas futuras do usuário e listas de barbearias recomendadas e populares.
- **Busca de barbearias (`/barbershops`)**: pesquisa por nome da barbearia ou por serviço. As categorias rápidas incluem cabelo, bigode, acabamento, sobrancelha, massagem e hidratação.
- **Detalhes da barbearia (`/barbershops/[id]`)**: apresenta endereço, descrição, serviços, preços e telefones para contato. Os telefones podem ser copiados.
- **Agendamento de serviço**: permite escolher uma data e um horário disponível entre 08:00 e 18:00. É necessário entrar com uma conta Google para confirmar a reserva.
- **Gerenciamento de reservas (`/bookings`)**: separa reservas futuras das concluídas, mostra os detalhes do serviço e da barbearia e permite cancelar ou excluir uma reserva.
- **Autenticação**: login e logout com Google via NextAuth. As reservas são associadas ao usuário autenticado.

## Tecnologias

- Next.js 14 e React 18
- TypeScript e Tailwind CSS
- NextAuth para autenticação com Google
- Prisma e PostgreSQL para persistência
- Radix UI, componentes próprios e Sonner para a interface e notificações

## Configuração local

1. Instale as dependências:

   ```bash
   npm install
   ```

2. Crie um arquivo `.env` na raiz e configure as variáveis:

   ```env
   DATABASE_URL="sua_url_de_conexao_postgresql"
   GOOGLE_CLIENT_ID="seu_client_id_google"
   GOOGLE_CLIENT_SECRET="seu_client_secret_google"
   NEXT_AUTH_SECRET="um_segredo_forte"
   ```

   Configure também no Google OAuth a URL de callback local:
   `http://localhost:3000/api/auth/callback/google`.

3. Aplique as migrações do Prisma usando o schema em `app/prisma/schema.prisma`. Para carregar os dados de demonstração, execute:

   ```bash
   npx tsx app/prisma/seed.ts
   ```

4. Inicie o servidor de desenvolvimento:

   ```bash
   npm run dev
   ```

   Acesse [http://localhost:3000](http://localhost:3000).

## Scripts disponíveis

| Comando | Descrição |
| --- | --- |
| `npm run dev` | Inicia o servidor de desenvolvimento. |
| `npm run build` | Gera a versão de produção. |
| `npm run start` | Inicia a aplicação compilada. |
| `npm run lint` | Executa o lint do Next.js. |

## Organização da aplicação

- `app/page.tsx`: página inicial.
- `app/barbershops/`: listagem, busca e detalhes de barbearias.
- `app/bookings/`: visualização de reservas.
- `app/actions/`: operações de criação, consulta de horários e exclusão de reservas.
- `app/data/`: consultas de barbearias e reservas.
- `app/components/`: componentes da interface, incluindo busca, serviços, cartões e navegação.
- `app/lib/`: configuração do Prisma e da autenticação.
- `app/prisma/`: schema, migrações e dados de demonstração.
