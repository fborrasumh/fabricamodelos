# Fábrica de modelos de lenguaje

Una página web que explica cómo se construye un modelo de lenguaje **montando uno de
verdad delante del usuario**. No hay vídeo ni simulación: el Transformer se entrena en
JavaScript dentro del navegador, con retropropagación escrita desde cero y sin ninguna
librería externa.

**App:** https://fborrasumh.github.io/fabricamodelos/

Material didáctico construido sobre el proyecto
[MiniMind](https://github.com/jingyaogong/minimind) (Jingyao Gong, Apache 2.0),
pensado para estudiantes de secundaria y primeros cursos de grado.

## Las siete etapas

1. **Trocear el texto** — algoritmo BPE paso a paso sobre el texto que escriba el
   estudiante, y el cálculo de por qué un modelo pequeño necesita un vocabulario pequeño.
2. **Montar la máquina** — las cuatro piezas del Transformer: atención causal, RoPE,
   RMSNorm y SwiGLU.
3. **Entrenar** — preentrenamiento real sobre 72 frases, con la curva de pérdida en vivo
   y las frases que el modelo va escribiendo según mejora.
4. **Mirar dentro** — mapa de atención por capa y por cabeza, con la máscara causal visible.
5. **Enseñar a conversar** — ajuste con 36 conversaciones (SFT): las mismas preguntas
   antes y después.
6. **Poner nota** — aprendizaje por refuerzo con una función de recompensa que el
   estudiante edita con deslizadores. Las alucinaciones aparecen solas y se marcan.
7. **Guardar y usar** — descarga del modelo a un archivo, borrado de memoria, recarga y
   chat, con la huella de los parámetros antes y después para ver que la inferencia no
   los toca.

## Detalles técnicos

- Un único fichero HTML, sin dependencias (solo las tipografías de Google, opcionales).
- Modelo: Transformer decoder-only, 3 capas, dimensión 32, 4 cabezas, 32.768 parámetros.
- Motor propio de autodiferenciación sobre matrices: matmul, RMSNorm, RoPE, softmax
  causal, SwiGLU, entropía cruzada y Adam. Gradientes verificados contra diferencias
  finitas.
- Entrenamiento completo en 10–20 segundos en un portátil corriente. No requiere GPU,
  ni claves de API, ni conexión.

## Licencia

MIT. Véase [LICENSE](LICENSE).
