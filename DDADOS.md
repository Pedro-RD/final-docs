# Dicionário de Dados

### Utilizador

| Campo         | Tipo   | Descrição                         | PK  | FK  |
| ------------- | ------ | --------------------------------- | --- | --- |
| id            | int    | Identificador único do utilizador | ✔   |     |
| nome          | string | Nome do utilizador                |     |     |
| email         | string | Email do utilizador               |     |     |
| password      | string | Password do utilizador            |     |     |
| morada        | string | Endereço do utilizador            |     |     |
| cidade        | string | Cidade do utilizador              |     |     |
| codigo_postal | string | Código postal                     |     |     |
| telefone      | string | Número de telefone                |     |     |
| nif           | string | Número de identificação fiscal    |     |     |
| role          | string | Função ou tipo de utilizador      |     |     |

### Funcionario

| Campo        | Tipo    | Descrição                | PK  | FK         |
| ------------ | ------- | ------------------------ | --- | ---------- |
| idUtilizador | int     | Referência ao utilizador | ✔   | Utilizador |
| salario      | decimal | Salário do funcionário   |     |            |

### Cuidador

| Campo        | Tipo | Descrição                              | PK  | FK          |
| ------------ | ---- | -------------------------------------- | --- | ----------- |
| idUtilizador | int  | Identificador do funcionario associado | ✔   | Funcionario |
| defaultTurno | int  | Turno padrão para o cuidador           |     | Turno       |

### Turno

| Campo      | Tipo     | Descrição                    | PK  | FK  |
| ---------- | -------- | ---------------------------- | --- | --- |
| id         | int      | Identificador único do turno | ✔   |     |
| descricao  | string   | Descrição do turno           |     |     |
| horaInicio | DateTime | Hora de início do turno      |     |     |
| horaFim    | DateTime | Hora de término do turno     |     |     |

<div class="page"/>

### AtribuicaoTurno

| Campo      | Tipo     | Descrição                         | PK  | FK       |
| ---------- | -------- | --------------------------------- | --- | -------- |
| id         | int      | Identificador único da atribuição | ✔   |          |
| data       | DateTime | Data da atribuição do turno       |     |          |
| idTurno    | int      | Identificador do turno            |     | Turno    |
| idCuidador | int      | Identificador do cuidador         |     | Cuidador |

### FamiliarResidente

| Campo        | Tipo | Descrição                             | PK  | FK         |
| ------------ | ---- | ------------------------------------- | --- | ---------- |
| id           | int  | Identificador                         | ✔   |            |
| idUtilizador | int  | Identificador do utilizador associado |     | Utilizador |
| idResidente  | int  | Identificador do residente associado  |     | Residente  |

### Residente

| Campo                 | Tipo     | Descrição                          | PK  | FK  |
| --------------------- | -------- | ---------------------------------- | --- | --- |
| id                    | int      | Identificador único do residente   | ✔   |     |
| nome                  | string   | Nome do residente                  |     |     |
| dataNascimento        | DateTime | Data de nascimento                 |     |     |
| EstadoCivil           | enum     | Estado civil do residente          |     |     |
| NumeroUtente          | int      | Número de utente                   |     |     |
| NumeroFiscal          | string   | Número de identificação fiscal     |     |     |
| Mobilidade            | enum     | Mobilidade do residente            |     |     |
| Dieta                 | enum     | Tipo de dieta                      |     |     |
| Alergias              | string   | Alergias do residente              |     |     |
| CuidadosEspeciais     | string   | Cuidados especiais necessários     |     |     |
| RestricoesAlimentares | string   | Restrições alimentares             |     |     |
| HistoricoClinico      | string   | Histórico clínico                  |     |     |
| Nacionalidade         | string   | Nacionalidade                      |     |     |
| Mensalidade           | decimal  | Mensalidade paga pelo residente    |     |     |
| FrequenciaRelatorio   | enum     | Frequência dos relatórios de saúde |     |     |
| NumeroCama            | int      | Número da cama                     |     |     |

<div class="page"/>

### Medicacao

| Campo       | Tipo   | Descrição                            | PK  | FK        |
| ----------- | ------ | ------------------------------------ | --- | --------- |
| id          | int    | Identificador da medicação           | ✔   |           |
| nome        | string | Nome da medicação                    |     |           |
| descricao   | string | Descrição da medicação               |     |           |
| quantidade  | int    | Quantidade disponível                |     |           |
| idResidente | int    | Identificador do residente associado |     | Residente |

### AdministracaoMedicacao

| Campo       | Tipo     | Descrição                             | PK  | FK        |
| ----------- | -------- | ------------------------------------- | --- | --------- |
| id          | int      | Identificador da administração        | ✔   |           |
| dataHora    | DateTime | Data e hora da administração          |     |           |
| Dosagem     | string   | Dosagem administrada                  |     |           |
| Observacoes | string   | Observações sobre a administração     |     |           |
| Estado      | enum     | Estado da administração               |     |           |
| idMedicacao | int      | Identificador da medicação            |     | Medicacao |
| idCuidador  | int      | Identificador do cuidador responsável |     | Cuidador  |

### ConsultaExterna

| Campo       | Tipo     | Descrição                            | PK  | FK        |
| ----------- | -------- | ------------------------------------ | --- | --------- |
| id          | int      | Identificador da consulta            | ✔   |           |
| dataHora    | DateTime | Data e hora da consulta              |     |           |
| descricao   | string   | Descrição da consulta                |     |           |
| observacoes | string   | Observações da consulta              |     |           |
| idResidente | int      | Identificador do residente associado |     | Residente |

<div class="page"/>

### RelatorioDeSaude

| Campo                       | Tipo     | Descrição                       | PK  | FK        |
| --------------------------- | -------- | ------------------------------- | --- | --------- |
| id                          | int      | Identificador do relatório      | ✔   |           |
| dataHora                    | DateTime | Data e hora do relatório        |     |           |
| temperatura                 | decimal  | Temperatura do residente        |     |           |
| altura                      | decimal  | Altura do residente             |     |           |
| peso                        | decimal  | Peso do residente               |     |           |
| frequenciaRespiratoria      | int      | Frequência respiratória         |     |           |
| frequenciaCardiaca          | int      | Frequência cardíaca             |     |           |
| nivelGlicose                | decimal  | Nível de glicose                |     |           |
| mobilidade                  | string   | Nível de mobilidade             |     |           |
| nivelHidratacao             | string   | Nível de hidratação             |     |           |
| avaliacaoCognitivaEmocional | string   | Avaliação cognitiva e emocional |     |           |
| observacoes                 | string   | Observações adicionais          |     |           |
| idResidente                 | int      | Identificador do residente      |     | Residente |
| nivelDeOxigenioNoSangue     | decimal  | Nível de oxigénio no sangue     |     |           |

### Mensagem

| Campo       | Tipo     | Descrição                  | PK  | FK         |
| ----------- | -------- | -------------------------- | --- | ---------- |
| id          | int      | Identificador da mensagem  | ✔   |            |
| assunto     | string   | Assunto da mensagem        |     |            |
| conteudo    | string   | Conteúdo da mensagem       |     |            |
| dataHora    | DateTime | Data e hora da mensagem    |     |            |
| idRemetente | int      | Identificador do remetente |     | Utilizador |

<div class="page"/>

### Resposta

| Campo       | Tipo     | Descrição                  | PK  | FK         |
| ----------- | -------- | -------------------------- | --- | ---------- |
| id          | int      | Identificador da resposta  | ✔   |            |
| conteudo    | string   | Conteúdo da resposta       |     |            |
| dataHora    | DateTime | Data e hora da resposta    |     |            |
| idMensagem  | int      | Identificador da mensagem  |     | Mensagem   |
| idRemetente | int      | Identificador do remetente |     | Utilizador |

### Alerta

| Campo        | Tipo     | Descrição                               | PK  | FK         |
| ------------ | -------- | --------------------------------------- | --- | ---------- |
| id           | int      | Identificador do alerta                 | ✔   |            |
| tipo         | enum     | Tipo de alerta                          |     |            |
| estado       | enum     | Estado do alerta                        |     |            |
| descricao    | string   | Descrição do alerta                     |     |            |
| dataHora     | DateTime | Data e hora do alerta                   |     |            |
| idUtilizador | int      | Identificador do utilizador relacionado |     | Utilizador |
| idResidente  | int      | Identificador do residente relacionado  |     | Residente  |

### Pagamento

| Campo       | Tipo     | Descrição                              | PK  | FK        |
| ----------- | -------- | -------------------------------------- | --- | --------- |
| id          | int      | Identificador do pagamento             | ✔   |           |
| data        | DateTime | Data do pagamento                      |     |           |
| valor       | decimal  | Valor do pagamento                     |     |           |
| observacoes | string   | Observações sobre o pagamento          |     |           |
| idResidente | int      | Identificador do residente relacionado |     | Residente |
