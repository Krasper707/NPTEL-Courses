## Toy example:

Vocabulary of an LLM:
- Although different LLMs have distinct vocabularies, given that these diverse vocabularies are learned from comparable corpora collected from the web, a substantial number of overlapping tokens naturally emerge. To illustrate this phenomenon, we record the rate of overlapping tokens between vocabularies of LLMs. As shown in Figure 3, the number of overlapping tokens is adequate. For example, TigerBot and LLaMA have 53% overlapping tokens. Intuitively, these overlapping tokens play a crucial role as a bridge to project diverse

Lets assume that the vocabulary is {I, love, Minecraft}

- P(I) = 0.4
- P(love | I) = 0.6
- P(I | love) = 0.03
- P( Minecraft | love I) = 0.0005
- P(Minecraft | I love) = 0.8
- So P(I love Minecraft) = 0.4 × 0.6 × 0.8 = 0.192. and P(Minecraft Love I ) = 0.4 * 0.03 * 0.0005 = 0.00006

```python
P_I = 0.4
P_love_given_I = 0.6
P_mc_given_Ilove = 0.8
P = P_I * P_love_given_I * P_mc_given_Ilove
print(P)
```



