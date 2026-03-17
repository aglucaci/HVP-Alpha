```mermaid
flowchart LR

    %% =========================
    %% Preprocessing
    %% =========================
    subgraph P1[Preprocessing]
        A["Data Input<br/><br/>Deliverables:<br/>• Raw FASTQ files<br/>• Sample metadata table"]
        B["Quality Control & Preprocessing<br/><br/>Deliverables:<br/>• Cleaned FASTQ files<br/>• QC reports<br/>• Summary metrics"]
        C["Host Read Removal<br/><br/>Deliverables:<br/>• Host-depleted FASTQ files<br/>• Host vs non-host stats<br/>• Alignment QC files"]

        A --> B --> C
    end

    %% =========================
    %% Profiling
    %% =========================
    subgraph P2[Profiling]
        D["Taxonomic Profiling<br/><br/>Deliverables:<br/>• Taxonomic abundance tables<br/>• Viral detection summary<br/>• Composition plots"]
        E["Viral Read Enrichment<br/><br/>Deliverables:<br/>• Viral-only FASTQ files<br/>• Viral read count tables"]

        C --> D --> E
    end

    %% =========================
    %% Genome Recovery
    %% =========================
    subgraph P3[Genome Recovery]
        F["Assembly<br/><br/>Deliverables:<br/>• Contig FASTA files<br/>• Assembly statistics<br/>• Coverage summaries"]
        G["Viral Identification & Annotation<br/><br/>Deliverables:<br/>• Annotated contigs/genomes<br/>• Feature tables<br/>• Viral genome catalog"]
        H["Read Mapping & Coverage Assessment<br/><br/>Deliverables:<br/>• Coverage plots<br/>• Mapping files<br/>• Completeness metrics"]

        E --> F --> G --> H
    end

    %% =========================
    %% Analysis
    %% =========================
    subgraph P4[Analysis]
        I["Variant Detection<br/><br/>Deliverables:<br/>• VCF files<br/>• Variant tables<br/>• Diversity metrics"]
        J["Recombination Analysis<br/><br/>Deliverables:<br/>• Breakpoint reports<br/>• Mosaic genome annotations<br/>• Recombination summaries"]
        K["Phylogenetic & Evolutionary Analysis<br/><br/>Deliverables:<br/>• Alignments<br/>• Phylogenetic trees<br/>• Selection/evolution metrics"]

        H --> I
        H --> J
        H --> K
    end

    %% =========================
    %% Output
    %% =========================
    subgraph P5[Reporting]
        L["Reporting & Integration<br/><br/>Deliverables:<br/>• Final report/dashboard<br/>• Figures and summary tables<br/>• Structured output files"]

        I --> L
        J --> L
        K --> L
    end

    %% =========================
    %% Styling
    %% =========================
    classDef group fill:#f8f9fa,stroke:#c9ced6,stroke-width:1px,color:#111;
    classDef start fill:#e8f1ff,stroke:#4a78c2,stroke-width:2px,color:#111;
    classDef process fill:#eef7ee,stroke:#4c8c4a,stroke-width:1.5px,color:#111;
    classDef analysis fill:#fff4e6,stroke:#d08b2d,stroke-width:1.5px,color:#111;
    classDef output fill:#f3e8ff,stroke:#8b5fbf,stroke-width:2px,color:#111;

    class P1,P2,P3,P4,P5 group;
    class A start;
    class B,C,D,E,F,G,H process;
    class I,J,K analysis;
    class L output;
