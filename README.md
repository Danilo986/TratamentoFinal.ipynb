---

## 📈 Lições Aprendidas & Engenharia de Produção (Melhores Práticas)

Após um processo de *code review*, foram identificadas e mapeadas importantes otimizações de arquitetura e performance para cenários de Big Data em produção. Essas melhorias elevam o projeto de um script acadêmico para um pipeline de dados otimizado:

### ⚡ 1. Otimização de Performance com Cache (`.cache()`)

<ul>
  <li><strong>Conceito Aplicado:</strong> O PySpark utiliza <em>Lazy Evaluation</em> (avaliação preguiçosa), o que significa que as transformações só são executadas quando uma ação (como um count ou write) é de fato chamada.</li>
  <li><strong>Solução Implementada:</strong> Inserção do método <code>.cache()</code> logo após o saneamento inicial dos dados (remoção de nulos e duplicados).</li>
</ul>

> **Resultado:** O DataFrame intermediário é persistido diretamente na memória RAM. Isso evita que o Spark precise reprocessar todo o grafo de execução (DAG) do zero a cada novo cruzamento ou exportação, gerando economia de tempo e de recursos computacionais.

---

### 🧩 2. Modularização e Clean Code (Funções Reutilizáveis)

<ul>
  <li><strong>Conceito Aplicado:</strong> Princípio de responsabilidade única e reaproveitamento de código (<em>DRY - Don't Repeat Yourself</em>).</li>
  <li><strong>Solução Proposta:</strong> Substituição de execuções sequenciais em células por funções puras e modulares (ex: <code>def limpar_dados_videos(df):</code>).</li>
</ul>

> **Resultado:** Facilidade extrema para manutenção do código, isolamento de bugs, ganho massivo em legibilidade no notebook e viabilização para a escrita de testes unitários automatizados.
