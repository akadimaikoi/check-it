O objetivo é configurar as regras de proteção no GitHub para as branches main e dev para garantir o seguinte fluxo:

Desenvolvimento acontece em branches de feature (feat/*) ou correção (fix/*).
Mudanças das branches feat/* ou fix/* são integradas na branch dev via Pull Request, exigindo aprovação de pelo menos 2 pessoas.
A branch main só pode receber atualizações diretamente da branch dev, também via Pull Request. Outras branches não conseguirão criar PRs diretamente para main.

## Fluxo Visual Simplificado

```mermaid
graph LR
    subgraph Desenvolvimento
        A[feat/*] --> B(Pull Request)
        C[fix/*] --> B
    end
    B --> D[dev]
    D --> E(Pull Request de dev para main)
    E --> F[main]
    %% Restrições visuais (opcional, pode ser explicado no texto)
    classDef restricted fill:#f9f,stroke:#333,stroke-width:2px;
    A --x F:::restricted
    C --x F:::restricted

```

*Note: O diagrama acima é uma representação simplificada. A exigência de 2 aprovações no PR para `develop` e as restrições diretas para `master` são garantidas pelas regras de proteção do GitHub.*

