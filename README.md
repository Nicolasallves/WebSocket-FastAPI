# WebSocket-FastAPI
Diferença entre requisições( http, push, full-duplex, ...)

Utilizar o seguinte comando no terminal para executar o programa e validar as chamadas:

uvicorn app:app --reload  


1 - Requisição simples HTTP(Page estatica):

http://localhost:8000/static

2 - Requisição para carregar tópicos por demanda, como exemplo utilizado no projeto, após apertar um botão uma nova requisição é feita.

http://localhost:8000/dynamic

3 - Requisição utilizando Polling, no projeto foi passado um timer de 5 segundos, então a cada 5 segundos é gerado um numero aleatório.

http://localhost:8000/polling

4 - Requisição full-duplex, no projeto foi criado um chat semelhante ao chat da UOL, foi utilizado broadcast para transmitir a mesma informação em realtime para todos os afetados.

Foi utilizado o método post para atualizar os dados e alterar a informação que estava sendo apresentada em tela.

método post:

        @push_router.post('/push')
        async def route_b(
                message: Message, response_model=Message
        ):
            await ws_manager.broadcast(message.message)
            return {'message': 'ok'}

http://localhost:8000/push


5 - Criação do chat, a informação inputada no chat é transmitida a todos os usuários que estiverem com o site aberto, sendo assim, uma transmissão em realtime dos dados para todas as pessoas utilizando a aplicação.


http://localhost:8000/duplex


