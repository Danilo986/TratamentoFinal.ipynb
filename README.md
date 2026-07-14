---

## 📈 Lições Aprendidas & Engenharia de Produção (Melhores Práticas)

Após um processo de *code review*, foram identificadas e mapeadas importantes otimizações de arquitetura e performance para cenários de Big Data em produção. Essas melhorias elevam o projeto de um script acadêmico para um pipeline de dados otimizado:

### ⚡ 1. Otimização de Performance com Cache (`.cache()`)

* **Conceito Aplicado:** O PySpark utiliza *Lazy Evaluation* (avaliação preguiçosa), o que significa que as transformações só são executadas quando uma ação (como gravar ou contar) é chamada.

* **Solução Implementada:** Inserção do método `.cache()` logo após o saneamento inicial dos dados (remoção de nulos e duplicados).

* **Resultado Prático:** O DataFrame intermediário é persistido diretamente na memória RAM. Isso evita que o Spark precise reprocessar todo o grafo de execução (DAG) do zero a cada novo cruzamento ou exportação, gerando economia de tempo e de recursos computacionais.

---

### 🧩 2. Modularização e Clean Code (Funções Reutilizáveis)

* **Conceito Aplicado:** Princípio de responsabilidade única e reaproveitamento de código (*DRY - Don't Repeat Yourself*).

* **Solução Proposta:** Substituição de execuções sequenciais em células por funções puras e modulares (ex: `def limpar_dados_videos(df):`).

* **Resultado Prático:** Facilidade extrema para manutenção do código, isolamento de bugs, ganho massivo em legibilidade no notebook e viabilização para a escrita de testes unitários automatizados.
