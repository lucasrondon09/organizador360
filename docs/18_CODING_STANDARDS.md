# ORGANIZADOR360
# CODING STANDARDS

Versão: 1.0  
Status: Oficial  
Data: 2026-07-10

---

# 1. Objetivo

Este documento define os padrões oficiais de desenvolvimento de código do Organizador360.

O objetivo é garantir:

- legibilidade;
- manutenção simplificada;
- consistência;
- segurança;
- facilidade de evolução;
- compatibilidade com desenvolvimento assistido por IA.

---

# 2. Princípios Gerais

Todo código deve seguir:

- simples é melhor que complexo;
- código deve ser compreendido por humanos;
- evitar duplicação;
- responsabilidade única;
- baixo acoplamento;
- alta coesão.

---

# 3. Idioma do Código

O código deverá utilizar:

## Inglês

Para:

- nomes de classes;
- funções;
- variáveis;
- tabelas;
- campos;
- endpoints;
- arquivos técnicos.

---

## Português

Permitido para:

- documentação;
- comentários explicativos;
- textos exibidos ao usuário.

---

# 4. Nomenclatura Geral

Utilizar nomes descritivos.

Evitar:

```
x
tmp
data2
aux
```

Preferir:

```
vehicle
maintenanceHistory
expirationDate
userProfile
```

---

# 5. Classes

Utilizar PascalCase.

Exemplo:

```python
class VehicleRepository:
    pass
```

---

Classes devem representar conceitos.

Evitar:

```
Manager
Helper
Utils
Common
```

sem contexto claro.

---

# 6. Funções e Métodos

Utilizar camelCase no Flutter.

Exemplo:

```dart
loadVehicles()
calculateExpirationDate()
```

Python:

utilizar snake_case.

Exemplo:

```python
calculate_expiration_date()
```

---

# 7. Variáveis

Devem representar seu conteúdo.

Ruim:

```python
d = 30
```

Bom:

```python
expiration_days = 30
```

---

# 8. Constantes

Utilizar letras maiúsculas.

Exemplo:

```python
MAX_UPLOAD_SIZE = 10485760
```

---

# 9. Arquivos

Nomes devem ser descritivos.

Exemplo:

```
vehicle_repository.py

maintenance_service.dart
```

Evitar:

```
service1.py

test_new.py
```

---

# 10. Organização de Código

Cada arquivo deve possuir responsabilidade única.

Evitar arquivos gigantes.

Quando um arquivo ultrapassar complexidade aceitável:

- dividir responsabilidades;
- criar novos componentes;
- manter organização modular.

---

# 11. Comentários

Comentários devem explicar:

- decisões;
- regras complexas;
- motivos técnicos.

Não explicar código óbvio.

Ruim:

```python
# soma dois números
total = a + b
```

---

Bom:

```python
# Mantém histórico para auditoria financeira
```

---

# 12. Documentação de Código

Código público deve possuir documentação.

Exemplo:

Python:

```python
def create_vehicle():
    """
    Creates a new user vehicle.
    """
```

---

# 13. Tratamento de Erros

Nunca ignorar exceções.

Ruim:

```python
try:
    process()
except:
    pass
```

---

Correto:

```python
try:
    process()
except ValidationError as error:
    raise ApplicationError(error)
```

---

# 14. Mensagens de Erro

Devem ser:

- claras;
- úteis;
- sem informações internas.

Nunca expor:

- SQL;
- caminhos internos;
- stack trace para usuário final.

---

# 15. Logs

Logs devem possuir:

- contexto;
- identificação;
- nível correto.

Níveis:

```
DEBUG

INFO

WARNING

ERROR

CRITICAL
```

---

# 16. Código Backend Python

Padrões obrigatórios:

- PEP8;
- Type Hints;
- Docstrings;
- Linters;
- Tipagem estática.

---

Exemplo:

```python
def get_vehicle(
    vehicle_id: UUID
) -> Vehicle:
    pass
```

---

# 17. Código Flutter/Dart

Padrões obrigatórios:

- Dart Effective Style;
- null safety;
- widgets pequenos;
- separação de responsabilidades.

---

Evitar:

Widgets com centenas de linhas.

---

# 18. Regras de Arquitetura

Código deve respeitar:

```
Presentation

↓

Application

↓

Domain

↓

Infrastructure
```

---

Dependências devem apontar para dentro.

---

# 19. Banco de Dados

Regras:

- migrations versionadas;
- nomes claros;
- índices justificados;
- constraints definidas.

---

# 20. APIs

Endpoints devem:

- possuir documentação;
- validar entrada;
- retornar respostas padronizadas;
- possuir testes.

---

# 21. Código Seguro

Nunca inserir diretamente:

- senhas;
- tokens;
- chaves;
- credenciais.

---

# 22. Dependências

Antes de adicionar biblioteca:

Avaliar:

- necessidade;
- manutenção;
- segurança;
- impacto.

---

# 23. Refatoração

Refatorações devem:

- melhorar código;
- manter comportamento;
- possuir testes.

---

# 24. Código Gerado por IA

Todo código gerado por IA deverá:

- seguir este documento;
- ser revisado;
- possuir testes;
- evitar complexidade desnecessária.

---

# 25. Qualidade Mínima

Antes de aprovação:

Código deve possuir:

- lint aprovado;
- testes executados;
- documentação atualizada;
- revisão realizada.

---

# 26. Code Smells

Evitar:

- funções enormes;
- classes gigantes;
- duplicação;
- lógica espalhada;
- dependências circulares.

---

# 27. Performance

Considerar:

- consultas eficientes;
- uso adequado de memória;
- carregamento sob demanda;
- cache quando necessário.

---

# 28. Segurança

Sempre validar:

- entradas;
- permissões;
- dados externos;
- uploads.

---

# 29. Checklist de Código

Antes do merge:

- [ ] nomes claros
- [ ] código organizado
- [ ] sem duplicação
- [ ] testes criados
- [ ] erros tratados
- [ ] segurança validada
- [ ] documentação atualizada

---

# 30. Considerações Finais

O padrão de código do Organizador360 tem como objetivo garantir que o projeto permaneça sustentável durante seu crescimento.

Qualquer código produzido por humanos ou inteligência artificial deverá seguir estas regras.

---

# FIM DO DOCUMENTO