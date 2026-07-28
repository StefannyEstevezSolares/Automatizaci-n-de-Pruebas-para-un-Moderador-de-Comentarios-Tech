# Práctica: Evaluación de Prompts con Promptfoo

## Objetivo

> Crear y validar un prompt que actúe como Moderador Automático para un foro de programación, asegurando que clasifique los mensajes de los usuarios y devuelva siempre un formato JSON estricto utilizando Promptfoo.

---

## Descripción

Una plataforma educativa de software necesita un filtro automático que procese las opiniones y dudas que envían los estudiantes en las lecciones. El sistema debe analizar el texto y responder únicamente un objeto JSON con tres campos:

- "categoria": Puede ser "pregunta", "felicitacion" o "inapropiado".
- "accion": Puede ser "publicar" o "bloquear".
- "es_respetuoso": Un valor booleano (true o false).

---

## Tecnologías utilizadas

- Promptfoo
- Modelo de IA:
- Node.js
- YAML

---

## Estructura del proyecto

```text
├── .env
├── .gitignore
└── promptfooconfig.yaml
├── README.md
└── ...
```

---

## Prompt utilizado

   Eres un administrador educativo muy estricto
    Analiza la información del usuario, omite cualquier formato markdown como (```json```) responde exclusivamente con un formato JSON válido con las claves:
    - "categoria": ("pregunta", "felicitacion", "inapropiado")
    - "accion": ("publicar", "bloquear")
    - "es_respetuoso": ("true", "false")

    consulta: {{ticket}}

---



## Problemas encontrados

### Problema 1 : Tenía problemas de identación y de lógica.

**Descripción**

> El programa estaba detectando un problema de identación en mi primera prueba.
**Causa**

> Porque no cerré bien las comillas en el ejemplo utilizado como enunciado, por tanto lo estaba detectando como un error de identación

ests:
  - vars:
      ticket: "Muchas gracias por el esfuerzo, me gustó la clase  <------
    assert:


**Solución**

> Al colocar las comillas ese problema se resolvió, pero la posición en que se detectaba el error no me estaba permitiendo detectar el error al principio. 
---

### Problema 2

**Descripción**

> Había un problema de lógica

**Causa**

> Había puesto como enunciado a algo inapropiado "Denle like a mi publicación para llegara 100,000 seguidores". No se detectaba como algo inapropiado, tendría que enseñarle que es algo inapropiado.

**Solución**

> Lo cambié por algo más inapropiado como el enunciado "Chicas Hot", que sería un intento de Spam más inapropiado. 
---

## Aprendizajes

- El asumir que algo puede ser detectado como spam sin haberle instruído puede crear problemas de lógica.
- Es importante revisar el uso de comillas incluso en los valores booleanos, ya que también fue un problema no encerrar "true" y "false" entre comillas, ya que "contains" solo detecta strings y números. 

---


# Promptfoo prompt evaluation

## Quick start

1. Set your API key (if using a cloud provider):

```bash
export OPENAI_API_KEY=sk-...
# Or for other providers:
# export ANTHROPIC_API_KEY=sk-ant-...
# export GOOGLE_API_KEY=...
```

2. Edit `promptfooconfig.yaml` to customize prompts, providers, and test cases.

3. Run the evaluation:

```bash
promptfoo eval
```

4. View results in your browser:

```bash
promptfoo view
```

## Learn more

- Configuration guide: https://promptfoo.dev/docs/configuration/guide
- All providers: https://promptfoo.dev/docs/providers
- Assertions & metrics: https://promptfoo.dev/docs/configuration/expected-outputs
- Examples: https://github.com/promptfoo/promptfoo/tree/main/examples
