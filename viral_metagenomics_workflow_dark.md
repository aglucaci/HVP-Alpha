
```mermaid
flowchart LR

    %% =========================
    %% Preprocessing
    %% =========================
    subgraph P1[Preprocessing]
        A["Data Input<br/><br/><span style='font-size:18px'>
        • Raw FASTQ files<br/>
        • Sample metadata
        </span>"]

        B["Quality Control<br/><br/><span style='font-size:18px'>
        • Cleaned reads<br/>
        • QC reports<br/>
        • Read metrics
        </span>"]

        C["Host Removal<br/><br/><span style='font-size:18px'>
        • Host-depleted reads<br/>
        • Alignment stats
        </span>"]

        A --> B --> C
    end

    %% =========================
    %% Profiling
    %% =========================
    subgraph P2[Profiling]
        D["Taxonomic Profiling<br/><br/><span style='font-size:18px'>
        • Abundance tables<br/>
        • Viral detection summary
        </span>"]

        E["Viral Read Selection<br/><br/><span style='font-size:18px'>
        • Viral FASTQ subset<br/>
        • Read counts
        </span>"]

        C --> D --> E
    end

    %% =========================
    %% Genome Recovery
    %% =========================
    subgraph P3[Genome Recovery]
        F["Assembly<br/><br/><span style='font-size:18px'>
        • Contig FASTA<br/>
        • Assembly statistics<br/>
        • Coverage summaries
        </span>"]

        G["Annotation<br/><br/><span style='font-size:18px'>
        • Annotated genomes<br/>
        • Gene/feature tables
        </span>"]

        H["Coverage Assessment<br/><br/><span style='font-size:18px'>
        • Depth & breadth<br/>
        • Completeness metrics
        </span>"]

        E --> F --> G --> H
    end

    %% =========================
    %% Analysis
    %% =========================
    subgraph P4[Analysis]
        I["Variant Detection<br/><br/><span style='font-size:18px'>
        • VCF files<br/>
        • Variant tables<br/>
        • Diversity metrics
        </span>"]

        J["Recombination<br/><br/><span style='font-size:18px'>
        • Breakpoints<br/>
        • Mosaic genomes
        </span>"]

        K["Phylogeny & Evolution<br/><br/><span style='font-size:18px'>
        • Alignments<br/>
        • Trees<br/>
        • Selection metrics
        </span>"]

        H --> I
        H --> J
        H --> K
    end

    %% =========================
    %% Output
    %% =========================
    subgraph P5[Output]
        L["Reporting<br/><br/><span style='font-size:18px'>
        • Dashboard / report<br/>
        • Figures<br/>
        • Structured data
        </span>"]

        I --> L
        J --> L
        K --> L
    end

    %% =========================
    %% Styling (Dark Mode)
    %% =========================
    classDef group fill:#0f172a,stroke:#334155,stroke-width:1px,color:#e5e7eb;

    classDef start fill:#1e3a8a,stroke:#3b82f6,stroke-width:2px,color:#e0f2fe;
    classDef process fill:#064e3b,stroke:#10b981,stroke-width:1.5px,color:#d1fae5;
    classDef analysis fill:#78350f,stroke:#f59e0b,stroke-width:1.5px,color:#fef3c7;
    classDef output fill:#581c87,stroke:#a855f7,stroke-width:2px,color:#f3e8ff;

    class P1,P2,P3,P4,P5 group;
    class A start;
    class B,C,D,E,F,G,H process;
    class I,J,K analysis;
    class L output;
