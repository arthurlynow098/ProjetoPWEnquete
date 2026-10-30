<p align="center">
  <img src="assets/banner-v2.png" alt="ProjetoPWEnquete" width="100%">
</p>

<p align="center">Plataforma de enquetes com autenticação, perfis de acesso e persistência em SQL Server.</p>

<p align="center"><img src="assets/docs/tags.svg" alt="C# · Identity · SQL Server" width="72%"></p>

<p align="center"><a href="#visão-geral">Visão geral</a> &nbsp;·&nbsp; <a href="#recursos">Recursos</a> &nbsp;·&nbsp; <a href="#como-executar">Como executar</a></p>

---

<a id="explore-o-projeto"></a>

![Explore o projeto](assets/docs/section-01.svg)

![Mapa visual dos arquivos e responsabilidades](assets/docs/map.svg)

| Área | O que você encontra | Acesso direto |
|---|---|---|
| **Enquetes** | Ações relacionadas às enquetes. | [Abrir enquetes →](ProjetoPWEnquete/Controllers/EnqueteController.cs) |
| **Banco de dados** | Contexto de persistência da aplicação. | [Abrir banco de dados →](ProjetoPWEnquete/Data/AppDbContext.cs) |
| **Conta** | Ações relacionadas ao acesso dos usuários. | [Abrir conta →](ProjetoPWEnquete/Controllers/AccountController.cs) |

<a id="visão-geral"></a>

![Visão geral](assets/docs/section-02.svg)

O sistema conta com controladores especializados para autenticação (AccountController), administração de enquetes (AdminEnquete), participação do usuário (UserEnquetesController) e exibição geral (EnqueteController), apoiados por um histórico detalhado de migrações do **Entity Framework Core**.

<a id="recursos"></a>

![Recursos](assets/docs/section-03.svg)

| Recurso | Como funciona |
|---|---|
| Painel Administrativo (AdminEnquete) | Criação, edição, ativação e encerramento de enquetes com acompanhamento de votos. |
| Área do Participante (UserEnquetesController) | Fluxo dedicado para visualização de enquetes disponíveis e registro seguro do voto. |
| Autenticação e Perfis (AccountController) | Gerenciamento de contas e sessões integrado ao banco de dados via Identity / EF Core. |
| Persistência SQL Server (AppDbContext) | Mapeamento relacional completo com mais de 10 migrações incrementais documentando a evolução do schema. |

<details>
<summary>Arquitetura</summary>

```mermaid
flowchart LR
    A["Usuário / Administrador"] --> B["AccountController · Autenticação"]
    B --> C["AdminEnquete · Gestão"]
    B --> D["UserEnquetesController · Votação"]
    C --> E["AppDbContext · EF Core"]
    D --> E
    E --> F["(SQL Server)"]
```

</details>

<details>
<summary>Estrutura do repositório</summary>

```text
ProjetoPWEnquete/
├── assets/
│   └── banner-v2.png               Banner do projeto
├── ProjetoPWEnquete/
│   ├── Controllers/                        Account, AdminEnquete, Enquete, Home e UserEnquetes
│   ├── Data/AppDbContext.cs                Contexto relacional do Entity Framework Core
│   ├── Migrations/                         Histórico evolutivo do schema SQL Server
│   ├── Models/ & Views/                    Entidades de domínio e telas Razor (.cshtml)
│   └── Program.cs                          Configuração de autenticação, EF Core e rotas
├── ProjetoPWEnquete.sln                    Solução Visual Studio
└── README.md
```

</details>

<a id="como-executar"></a>

![Como executar](assets/docs/section-04.svg)

1. Clone o repositório:
   ```powershell
   git clone https://github.com/arthurlynow098/ProjetoPWEnquete.git
   cd ProjetoPWEnquete
   ```
2. Configure sua string de conexão do **SQL Server** em ProjetoPWEnquete/appsettings.json.
3. Aplique as migrações e inicie a aplicação:
   ```powershell
   dotnet ef database update --project ProjetoPWEnquete
   dotnet run --project ProjetoPWEnquete/ProjetoPWEnquete.csproj
   ```

---

<p align="center">
  <a href="https://github.com/arthurlynow098">GitHub</a> &nbsp;·&nbsp;
  <a href="https://arthurentsev.vercel.app/">Portfólio</a> &nbsp;·&nbsp;
  <a href="https://www.linkedin.com/in/entsevarthur/">LinkedIn</a>
</p>
