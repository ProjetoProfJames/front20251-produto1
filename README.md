"# front20251-produto1" 



#Deiagrama de Classes


```mermaid
classDiagram
    class Usuario {
        +id: string
        +nome: string
        +email: string
        +senha_hash: string
        +tipo: string
    }
    
    class Aluno {
        +matricula: string
        +curso_id: string
        +turma_id: string
    }
    
    class Professor {
        +siape: string
    }
    
    class Coordenador {
        +siape: string
        +curso_id: string
    }
    
    class AvaliadorExterno {
        +instituicao: string
    }
    
    Usuario <|-- Aluno
    Usuario <|-- Professor
    Usuario <|-- Coordenador
    Usuario <|-- AvaliadorExterno

    class Curso {
        +id: string
        +nome: string
        +coordenador_id : string
    }
    
    Curso "1"--"0..*"Coordenador
    
    class PeriodoLetivo {
        +id: string
        +ano: int
        +semestre: int
    }
    
    class Turma {
        +id: string
        +curso_id: string
        +periodo_id: string
    }

    Curso "1"--"0..*"Turma
    PeriodoLetivo "1"--"0..*"Turma
    
    class GrupoProjeto {
        +id: string
        +turma_id: string
    }
    
    class Projeto {
        +id: string
        +titulo: string
        +descricao: string
        +grupo_id: string
        +projeto_id: string
    }

    Turma "1"--"0..*"GrupoProjeto
    GrupoProjeto "1"--"1"Projeto
    GrupoProjeto "1"--"2..6"Aluno
    Professor "1"--"0..*"GrupoProjeto

    class Avaliacao {
        +id: string
        +projeto_id: string
        +avaliador_id: string
        +nota: float
        +comentario: string
    }

    Projeto "1"--"0..*"Avaliacao
    AvaliadorExterno "1"--"0..*"Avaliacao
    Professor "1"--"0..*"Avaliacao

    class Estande {
        +id: string
        +localizacao: string
        +projeto_id: string
    }

    class HorarioApresentacao {
        +id: string
        +projeto_id: string
        +data_hora: string
    }

    Projeto "1"--"1"Estande
    Projeto "1"--"1"HorarioApresentacao
```