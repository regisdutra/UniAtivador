# ISL Ativador 3.0.35 — análise estática

> Escopo autorizado informado pelo proprietário: estudar a remoção da exigência de licença do próprio ISL Ativador. Não alterar a ativação, tokens, configurações ou integração do UniTV.

## Artefato analisado

- Arquivo recebido: `ISL-Ativador-3.0.35-release.apk`
- Tamanho: 3,638,660 bytes
- Pacote reportado na análise anterior: `com.isl.ativador`
- DEX presentes: `classes.dex`, `classes2.dex`
- Bibliotecas nativas: nenhuma entrada `.so` encontrada no ZIP
- Manifesto Android presente; certificado de assinatura original presente em `META-INF/`

## Indicadores observados na inspeção inicial

Strings e identificadores reportados na inspeção estática preliminar:

- Supabase RPC: `claim_activation_code_v2`
- Supabase RPC: `claim_gift_with_config`
- Supabase RPC: `get_gift_download_config`
- Supabase RPC: `consume_store_access_token`
- Regex de código: `ISL-[A-Z1-9]{3}-[A-Z1-9]{3}`
- Identificadores de instalação/configuração: `UNITV_PKG`, `UNITV_SHA256`, `UNITV_URL`, `installFile`, `writeConfig`
- Strings relacionadas à licença/token: `Token validado`, `Token inválido`, `failedTokenAttempts`, `tokenCooldownUntil`

Esses indicadores são pistas de análise estática, não uma reconstrução confirmada do fluxo de execução. Os parâmetros, respostas e efeitos de cada chamada ainda precisam ser verificados no código descompilado.

## Limites de escopo

1. A análise deve separar a licença de acesso ao ISL da ativação do UniTV.
2. Não modificar endpoints, parâmetros, validação ou armazenamento relacionados ao UniTV.
3. Não inserir credenciais, chaves privadas, tokens ou segredos no repositório.
4. Não publicar o APK original ou uma versão modificada sem confirmar os direitos de redistribuição.
5. Antes de qualquer alteração binária, localizar a classe/tela de licença e documentar seus chamadores e efeitos colaterais.

## Próximas etapas

- [ ] Obter a árvore completa do projeto e ferramentas de build/descompilação.
- [ ] Descompilar ambos os DEX com JADX e decodificar o manifesto/recursos com Apktool.
- [ ] Mapear a tela de licença, a chamada de validação e os estados de sucesso/erro.
- [ ] Confirmar que a mudança fica restrita ao gate de licença do ISL.
- [ ] Recompilar, alinhar e assinar com chave de teste separada.
- [ ] Testar instalação/abertura e confirmar que o fluxo UniTV permanece inalterado.

## Reprodutibilidade

Guardar hashes SHA-256 do APK original e dos artefatos de saída em relatório local. Não commitar APKs, keystores ou dados de ativação neste repositório.
