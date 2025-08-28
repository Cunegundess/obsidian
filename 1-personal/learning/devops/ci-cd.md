# Material de CI/CD

Criado em: 3 de junho de 2025 11:48
Prioridade: Baixa
Status: Em andamento
Área: Estudos

<aside>
💡

Esta página é dedicada a anotações sobre meus estudos em CI/CD, incluindo ideias de possíveis formas de implementar essa metodologia na HB e em outros projetos.
O foco principal é o uso do GitLab CI/CD, embora os conceitos também possam ser aplicados com GitHub Actions.

**Pontos a serem observados:**

- Padronizar lint, formatação
- Possível refatoração antes de implementar alguma camada de testes
- Branch main para exclusivamente deploy e develop para testar se as features/merges estão funcionando devidamente
    - GitFlow
- Utilizar TDD em novas demanda
- O GitLab possui várias ferramentas nativas que podem ser úteis, como por exemplo, o quadro de issues
    - Pode ser útil na organização das tarefas e pontos de melhoria do projeto

**Importante:** 

- **Na HB, precisa usar a main como branch principal ao invés da Dev**
- **Automatizar para que faça a parte de CD nas janelas de atualização**
- **Na HB, implementar os testes unitários conforme o tempo pra ir aumentando a cobertura de testes**
    - **Talvez criar uma branch de testes pra poder cuidar disso**
</aside>

<aside>
📽️

**Vídeos de referência**

### GitLab CI/CD Pipeline Tutorial for Beginners

[https://www.youtube.com/watch?v=z7nLsJvEyMY](https://www.youtube.com/watch?v=z7nLsJvEyMY)

### DevOps with GitLab CI Course - Build Pipelines and Deploy to AWS

[https://www.youtube.com/watch?v=PGyhBwLyK2U](https://www.youtube.com/watch?v=PGyhBwLyK2U)

### GitLab CI CD automation (Docker, Kubernetes, Terraform, and more…)

[https://www.youtube.com/watch?v=zBrP8MzA5y0](https://www.youtube.com/watch?v=zBrP8MzA5y0)

</aside>

# Estrutura geral

Primeiro deve-se criar um arquivo **`.gitlab-ci.yml`** na raiz do projeto e definir os **`stages`** da esteira (estou adaptando o exemplo pra um possível uso na HB)

```yaml
stages:
	- push_to_gitlab
	- deploy_to_aws
```

Depois, defina as variáveis que vão ser utilizadas nesse processo

```yaml
variables:
	- HB_CONTAINER: "anytask-hb-tracer"
	- AWS_PROJECT_DIR: "$HOME/hb-tracer/"
	- SSH_KEY: "${SSH_KEY}" # Adicionar no gitlab
	- HOST_USER: ubuntu
	- HOST_IP: 35.175.55.32
	# outras possíveis variáveis
```

Agora, defina os processos referentes ao CI (Repositório no Gitlab)

```yaml
ci_gitlab:
  stage: push_to_gitlab
  image: alpine:latest
  only:
    - main
  script:
    - echo "🔍 Rodando esteira de CI na branch 'main'..."
```

Por último, defina os processos referentes ao CD (Deploy do Projeto na instância AWS)

```yaml
cd_deploy:
  stage: deploy_to_aws
  only:
    - main
  when: manual
  script:
    # Verifica se estamos na janela permitida (11h30 às 12h30 UTC)
    - |
      HOUR=$(date +"%H")
      if [[ "$HOUR" -ge 11:30 || "$HOUR" -lt 12:30 ]]; then
        echo "⏱ Dentro da janela de deploy permitida. Continuando..."
        ssh -i $SSH_KEY $HOST_USER@$HOST_IP << EOF
        echo "🛑 Parando container existente..."
        docker stop $DOCKER_CONTAINER_NAME || true
        echo "📥 Atualizando repositório..."
        cd $AWS_PROJECT_DIR
        git checkout main
        git fetch origin
        git pull origin main
        echo "🚀 Subindo aplicação com Docker Compose..."
        docker compose up -d --build
      EOF
      else
        echo "⛔ Fora da janela de deploy (11h30-12h30 UTC). Abortando pipeline."
        exit 1
      fi
```