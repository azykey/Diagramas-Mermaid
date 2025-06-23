

## 1. Use Temas e Estilização

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#ffd8d8', 'edgeLabelBackground':'#fff'}}}%%
graph TD
    A[Início] -->|Processo 1| B(Dados)
    B --> C{Decisão}
    C -->|Sim| D[Resultado A]
    C -->|Não| E[Resultado B]
```

## 2. Formatação Avançada de Texto

```mermaid
graph LR
    A[<b>Texto em Negrito</b><br/><i>Itálico</i>] --> B[<span style='color:red'>Texto Vermelho</span>]
```

## 3. Alinhamento e Layout

```mermaid
graph TB
    subgraph "Processo Principal"
    A --> B
    B --> C
    end
    
    subgraph "Subprocesso"
    D --> E
    E --> F
    end
    
    C --> D
```

## 4. Diagramas de Sequência Detalhados

```mermaid
sequenceDiagram
    participant A as Cliente
    participant B as Servidor
    
    A->>B: Requisição HTTP
    Note right of B: Processando...
    B-->>A: Resposta 200 OK
    B->>C: Consulta DB
```

## 5. Personalização de Formas

```mermaid
graph LR
    id1([Início]) --> id2[[Processo]]
    id2 --> id3[(Banco de Dados)]
    id3 --> id4{Decisão?}
    id4 -->|Sim| id5((Fim))
```

## 6. Uso de Classes CSS

```mermaid
classDiagram
    class Animal {
        <<interface>>
        +nome: string
        +mover()
    }
    
    class Cachorro {
        +raça: string
        +latir()
    }
    
    Animal <|-- Cachorro
```





# Diagramas Mermaid Avançados: Técnicas Profissionais


## 1. Diagramas de Arquitetura Complexos

```mermaid
graph TD
    subgraph "Cloud Environment"
        A[Load Balancer] --> B[API Gateway]
        B --> C[Microservice A]
        B --> D[Microservice B]
        
        subgraph "Data Layer"
            C --> E[(Database Cluster)]
            D --> E
            E --> F[Redis Cache]
        end
        
        B --> G[Auth Service]
        G --> H[OAuth 2.0 Provider]
    end
    
    Internet --> A
    style Internet fill:#fff,stroke:#333,stroke-width:2px
    style A fill:#9f9,stroke:#090
```

## 2. Diagramas de Sequência Detalhados com Loops e Alternativas

```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant Backend
    participant Database
    
    User->>Frontend: Submit Form
    Frontend->>Backend: POST /api/data
    alt Validation Success
        Backend->>Database: BEGIN TRANSACTION
        Backend->>Database: INSERT Data
        loop Retry Policy
            Backend->>ExternalService: Call API
            alt API Success
                ExternalService-->>Backend: 200 OK
            else API Failure
                ExternalService-->>Backend: 500 Error
                Backend->>Backend: Retry (3x)
            end
        end
        Backend->>Database: COMMIT
        Backend-->>Frontend: 201 Created
    else Validation Error
        Backend-->>Frontend: 400 Bad Request
    end
    Frontend-->>User: Show Result
```

## 3. Diagramas de Estado Complexos

```mermaid
stateDiagram-v2
    [*] --> Idle
    
    state PaymentProcess {
        [*] --> PaymentInitiated
        PaymentInitiated --> Processing: Submit Payment
        Processing --> Success: Payment Approved
        Processing --> Failure: Payment Declined
        
        state Success {
            [*] --> NotificationSent
            NotificationSent --> Completed: Receipt Generated
        }
        
        state Failure {
            [*] --> ErrorDisplayed
            ErrorDisplayed --> RetryOption
            RetryOption --> Processing: User Retries
            RetryOption --> Cancelled: User Cancels
        }
    }
    
    Idle --> PaymentProcess: Start Checkout
    PaymentProcess --> Idle: Return to Shop
```


## 5. Fluxo de CI/CD com Subgraphs Aninhados

```mermaid
graph LR
    subgraph "Developer"
        A[Local Commit] --> B[Push to Feature Branch]
    end
    
    subgraph "GitHub"
        B --> C{Pull Request}
        C -->|Approved| D[Merge to Main]
    end
    
    subgraph "CI Pipeline"
        D --> E[Build]
        E --> F[Unit Tests]
        F --> G[Integration Tests]
        G --> H[Package]
    end
    
    subgraph "CD Pipeline"
        H --> I[Staging Deployment]
        I --> J[Smoke Tests]
        J --> K[Canary Release]
        K --> L[Full Production Rollout]
    end
    
    subgraph "Monitoring"
        L --> M[Health Checks]
        M --> N[Logs & Metrics]
        N --> O[Alerting]
    end
    
    style Developer fill:#e6f3ff,stroke:#333
    style GitHub fill:#f0f0f0,stroke:#333
    style CI fill:#e6ffe6,stroke:#090
    style CD fill:#ffe6e6,stroke:#900
    style Monitoring fill:#fff2cc,stroke:#e69138
```

## 6. Personalização Extrema com CSS Direto

```mermaid
graph TD
    classDef highlight fill:#ff9,stroke:#f90,stroke-width:2px
    classDef critical fill:#f99,stroke:#900,stroke-width:3px
    classDef data fill:#9cf,stroke:#06c
    
    A[Início]:::highlight --> B{Processamento}
    B -->|Sucesso| C[(Banco)]:::data
    B -->|Falha| D[Alertar Admin]:::critical
    
    %% Estilo personalizado para setas
    linkStyle 0 stroke:#0a0,stroke-width:2px
    linkStyle 1 stroke:#a00,stroke-width:2px,stroke-dasharray:5
```


## 1. Diagrama de Rede Kubernetes (AKS/EKS)

```mermaid
graph TD
    subgraph "Cluster Kubernetes"
        subgraph "Node Pool 1"
            A[Pod A-1] -->|Service| B[Pod A-2]
            A --> C[Pod A-3]
            style A fill:#e1f5fe,stroke:#039be5
        end
        
        subgraph "Node Pool 2"
            D[Pod B-1] -->|gRPC| E[Pod B-2]
            E --> F[(Persistent Volume)]
        end
        
        G[Ingress Controller] --> A
        G --> D
        H[External DNS] --> G
    end
    
    subgraph "Serviços Gerenciados"
        I[(Azure CosmosDB)] --> D
        J[Azure Redis] --> A
        K[Monitor] -.->|Prometheus| A
        K -.-> D
    end
    
    Internet --> G
    style Internet fill:#fff,stroke:#333,stroke-width:2px
    
    classDef k8s fill:#326ce5,stroke:#fff,color:#fff
    classDef cloud fill:#ff9900,stroke:#fff
    classDef storage fill:#5c9eff,stroke:#003a75
    class A,B,C,D,E k8s
    class F,I storage
    class J,K cloud
```

## 3. Fluxo de Machine Learning (MLOps)

```mermaid
flowchart TB
    subgraph "Data Pipeline"
        A[Data Extraction] --> B[Data Validation]
        B --> C[Feature Engineering]
        C --> D[Feature Store]
    end
    
    subgraph "Model Training"
        D --> E[Experiment Tracking]
        E --> F[Hyperparameter Tuning]
        F --> G[Model Registry]
    end
    
    subgraph "Deployment"
        G --> H[Canary Deployment]
        H --> I[AB Testing]
        I --> J[Shadow Mode]
    end
    
    subgraph "Monitoring"
        J --> K[Data Drift Detection]
        K --> L[Model Retraining Trigger]
        L --> A
    end
    
    M[CI/CD Orchestrator] -.->|Triggers| E
    M -.-> H
    
    style A,B,C,D fill:#5e35b1,color:#fff
    style E,F,G fill:#3949ab,color:#fff
    style H,I,J fill:#1e88e5,color:#fff
    style K,L fill:#00897b,color:#fff
    style M fill:#f57c00,color:#000
```

## 4. Sistema Distribuído com Mensageria (Event-Driven)

```mermaid
graph LR
    subgraph "Service A"
        A[API] --> B[Command Handler]
        B --> C[Event Producer]
    end
    
    subgraph "Kafka Cluster"
        C --> D[Topic Orders]
        C --> E[Topic Payments]
        D --> F[Consumer Group 1]
        E --> G[Consumer Group 2]
    end
    
    subgraph "Service B"
        F --> H[Event Processor]
        H --> I[Projection]
        I --> J[Read Model]
    end
    
    subgraph "Service C"
        G --> K[Payment Saga]
        K -->|Compensating| L[Email Service]
    end
    
    subgraph "Observability"
        M[OpenTelemetry] -->|Traces| N[Jaeger]
        O[Prometheus] -->|Metrics| P[Grafana]
        Q[Fluentd] -->|Logs| R[Elasticsearch]
    end
    
    C -.-> M
    H -.-> M
    K -.-> O
    
    classDef service fill:#1976d2,color:#fff
    classDef kafka fill:#000,color:#fff
    classDef storage fill:#388e3c,color:#fff
    classDef monitoring fill:#d32f2f,color:#fff
    
    class A,B,C,H,K service
    class D,E,F,G kafka
    class I,J,L storage
    class M,N,O,P,Q,R monitoring
```

## Técnicas Avançadas Utilizadas:

1. **Hierarquia Visual** - Subgraphs aninhados para representar componentes lógicos
2. **Semântica de Cores** - Esquema de cores consistente por tipo de componente
3. **Estilos Personalizados** - classDef para padronização visual
4. **Tipos de Conexão** - Setas sólidas para fluxo principal, tracejadas para secundárias
5. **Notação Especial** - Ícones e símbolos para diferentes tipos de serviços
6. **Cross-Linking** - Conexões entre subgrafos distintos



1. **Formas mais elaboradas** (não apenas retângulos básicos)  
2. **Ícones e elementos visuais ricos**  
3. **Hierarquia visual clara**  
4. **Detalhes realistas**  

---


### 🛠️ **Soluções para o erro:**

1. **Remova elementos complexos** (ícones externos, HTML):
   ```mermaid
   graph TD
       subgraph "Cluster Kubernetes"
           A[Pod Frontend] --> B[Pod Backend]
           B --> C[(Redis)]
           D[Ingress] --> A
       end
       E[Internet] --> D
   ```

2. **Use a sintaxe Mermaid pura** (sem HTML/CSS externo):
   ```mermaid
   flowchart TB
       subgraph DataPipeline
           A[Data Sources] --> B[Preprocessing]
           B --> C[Feature Store]
       end
       C --> D[Model Training]
   ```


---

### ✨ **Versão Funcional do Kubernetes Diagram** (sem ícones):
```mermaid
graph TD
    subgraph "Cluster Kubernetes"
        subgraph "Namespace: Aplicação"
            A[Frontend Pod] -->|HTTP| B[Backend Pod]
            B --> C[(Redis)]
        end
        subgraph "Namespace: Sistema"
            D[Ingress-NGINX] --> A
            E[Prometheus] -. Monitora .-> A
            E -. Monitora .-> B
        end
    end
    F[Internet] --> D
    G[AWS RDS] --> B
    
    classDef pod fill:#e3f2fd,stroke:#64b5f6
    classDef storage fill:#fff3e0,stroke:#ffb74d
    class A,B pod
    class C,G storage
```




# Diagrama Avançado: Sistema de Detecção de Comportamento Anômalo (SentinelCore)

```mermaid
%%{init: {'theme': 'dark', 'fontFamily': 'Segoe UI', 'gantt': {'barHeight': 20}}}%%
flowchart TD
    subgraph "🖥️ Cliente"
        A[Game Client] --> B[Input Capture]
        B --> C[BehaviorTracker.cpp]
        C -->|Métricas| D[Local Analysis]
        D -->|Eventos Suspeitos| E[gRPC Stream]
    end

    subgraph "🔍 Servidor de Análise"
        E --> F[gRPC Gateway]
        F --> G[Real-Time Processor]
        G --> H[Anomaly Detection Engine]
        H -->|Model Input| I[AI Model]
        I --> J[Threat Scoring]
        J --> K[Decision Engine]
    end

    subgraph "📊 Backend Services"
        K -->|Log Suspicious| L[Case Database]
        K -->|Alert| M[Admin Dashboard]
        H --> N[Training Data Pipeline]
        N --> O[Model Retraining]
        O --> I
    end

    subgraph "🛡️ Sistema Anti-Tamper"
        P[File Integrity Monitor] -->|Hash Check| Q[Trusted Storage]
        P -->|Detect Changes| R[Violation Reporter]
        R --> K
        S[Memory Scanner] -->|Scan| T[Process Memory]
        S --> U[Pattern Detection]
        U --> K
    end

    style A fill:#4a148c,stroke:#ce93d8
    style C fill:#1a237e,stroke:#7986cb
    style I fill:#01579b,stroke:#4fc3f7
    style P fill:#bf360c,stroke:#ff8a65
    style M fill:#33691e,stroke:#aed581

    classDef client fill:#1e88e5,stroke:#90caf9
    classDef server fill:#00897b,stroke:#b2dfdb
    classDef backend fill:#5e35b1,stroke:#b39ddb
    classDef security fill:#e65100,stroke:#ffb74d

    class A,B,C,D,E client
    class F,G,H,J,K server
    class L,M,N,O backend
    class P,Q,R,S,T,U security
```

## Componentes Detalhados

### 1. Pipeline de Análise de Comportamento
```mermaid
sequenceDiagram
    participant Client as Game Client
    participant Tracker as BehaviorTracker
    participant Server as Analysis Server
    participant AI as AI Model

    Client->>Tracker: Input Events (Mouse/Keyboard)
    loop Every 50ms
        Tracker->>Tracker: Record Input Metrics
        Tracker->>Tracker: Calculate Statistics
    end
    Tracker->>Server: Stream Metrics (gRPC)
    Server->>AI: Prepare Feature Vector
    AI->>Server: Anomaly Score (0-1)
    alt Score > 0.85
        Server->>Server: Create Case
        Server->>Dashboard: Alert
    end
```

### 2. Arquitetura Anti-Tamper
```mermaid
classDiagram
    class FileIntegrityMonitor {
        +fileHashes: Map
        +checkFiles(): Violation[]
        +whitelist: string[]
    }

    class MemoryScanner {
        +signatures: CheatPattern[]
        +scanProcess(): Detection[]
        +deepScan(): boolean
    }

    class AntiTamperSystem {
        -fileMonitor: FileIntegrityMonitor
        -memoryScanner: MemoryScanner
        +start(): void
        +report(): ViolationReport
    }

    FileIntegrityMonitor "1" --> "1" AntiTamperSystem
    MemoryScanner "1" --> "1" AntiTamperSystem
```

### 3. Dashboard de Anomalias (Exemplo)
```mermaid
pie
    title Detecções por Tipo (Últimas 24h)
    "Reação Sobre-Humana" : 38
    "Padrões de Tiro Robóticos" : 45
    "Movimentos Impossíveis" : 17
    "Modificação de Arquivos" : 12
```

adilson oliveira
