# Previsão de Aluguel de Bicicletas com Azure Machine Learning

Este projeto utiliza o recurso de Machine Learning Automatizado do Azure Machine Learning para treinar e implantar um modelo de previsão de aluguéis de bicicletas.

## Etapas Realizadas

### 1. Criação do Workspace

1. Acesse [Azure Portal](https://portal.azure.com).
2. Crie um recurso do tipo **Machine Learning** com as configurações:
   - **Região:** Leste dos EUA.
   - **Conta de Armazenamento:** Criada automaticamente.

### 2. Treinamento do Modelo

1. No Azure Machine Learning Studio, acesse a aba **Automated ML**.

2. Crie um novo trabalho:

   - Nome: `bike-rental-prediction`.
   - Conjunto de Dados: `bike-rentals`.
   - Modelos Permitidos: RandomForest e LightGBM.
   - Métrica: NormalizedRootMeanSquaredError.

3. Execute o treinamento e aguarde a conclusão.

### 3. Implantação do Modelo

1. Acesse o melhor modelo treinado.

2. Clique em **Deploy** e configure o endpoint:

   - **Tipo de VM:** Standard\_DS3\_v2.
   - **Contagem de Instâncias:** 3.

3. Aguarde o status de implantação mudar para **Succeeded**.

### 4. Teste do Endpoint

1. Vá até a aba **Endpoints**.
2. Insira os seguintes dados JSON para teste:
   ```json
   {
     "input_data": {
       "columns": [
         "day", "mnth", "year", "season", "holiday", "weekday",
         "workingday", "weathersit", "temp", "atemp", "hum", "windspeed"
       ],
       "index": [0],
       "data": [[1, 1, 2022, 2, 0, 1, 1, 2, 0.3, 0.3, 0.3, 0.3]]
     }
   }
   ```
3. Verifique a saída (número de aluguéis previstos).

## Artefatos

- `endpoint.json`: Configurações do endpoint em tempo real.
- Este `README.md`.

---

**Observações:**

- Certifique-se de ter permissões adequadas no Azure para criar e implantar modelos.
- Se encontrar erros durante o treinamento ou implantação, revise as configurações do workspace e dos recursos criados.

Link para o Repositório: [GitHub](https://github.com/seu-repositorio)

https\://github.com/wedleycso/Microsoft---Fundamentos-de-IA.git

