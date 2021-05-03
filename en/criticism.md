# Crítica

## UDP nunca vai funcionar

Diversas empresas, operadores e organizações bloqueiam ou limitam a taxa de
tráfego do UDP para fora da porta 53 (usada para DNS) já que nos últimos dias
tem sido usado principalmente para ataques. Em particular, alguns protocolos
UDP e populares servers dele têm sido vulneráveis a ataques de amplificação 
em que um invasor pode fazer uma grande quantidade de tráfego para atingir vítimas inocentes.

QUIC tem mitigação embutida contra-ataques de amplificação por requerer um pacote
inicial que precisa ter pelo menos 1200 bytes e por restringir no protocolo que
diz que o servidor não pode mandar mais de três vezes o tamanho da request na resposta
sem receber um pacote do cliente.

## UDP é lento em kernels

Isso parece ser verdade, pelo menos inicialmente. Nós não podemos dizer como
isso se desenvolverá e quanto isso é simplesmente o resultado do desempenho de transferência 
não ter estado no foco dos desenvolvedores por muitos anos.

Para a maioria dos clientes, essa 'lentidão' provavelmente nunca é percetível.

## QUIC consume muito CPU

Similar a observação acima 'UDP é lento', isso ocorre em parte porque o uso do TCP 
e do TLS no mundo teve mais tempo para amadurecer, melhorar e obter assistência de hardware.

Existem razões para esperar que isso melhore com o tempo, e já [estamos vendo algumas
melhorias nesse espaço](https://www.fastly.com/blog/measuring-quic-vs-tcp-computational-efficiency).
A questão sobre o quanto de uso de CPU extra irá machucar deployers.

## Isso é apenas o Google

Não, não é. O Google trouxe a especificação inicial para o IETF (Internet Engineering Task Force)
após provar, em larga escala, que implantar esse estilo de protocolo sobre o UDP
funciona e tem um bom desempenho bem.

Desde então, indivíduos de um grande número de empresas e organizações tem trabalhado
com a IETF para montar um protocolo de transporte padrão a partir dele. Nesse trabalho,
funcionários do google, é claro, tem participado, mas também funcionarios de um grande 
número de outras empresas que estão interessadas em promover o estado dos protocolos de
transporte na Internet, como Mozilla, Fastly, Cloudflare, Akamai, Microsoft, Facebook e Apple.


## Esta é uma melhoria muito pequena

Isso não é realmente uma critica, mas uma opinião. Talvez seja, e talvez seja
uma melhoria muito pequena tão próxima no tempo desde que o HTTP2 foi lançado.

HTTP/3 é provável que tenha um desempenho muito melhor em redes movidas a perda de pacotes,
ele oferece handshakes mais rapidos, então isso irá melhorar a latencia percebida e real.
Mas isso é beneficios suficientes para motivar pessoas a implementarem o HTTP/3
nos seus servidores e nos seus serviços? Tempo e as medições de desempenho futuro irão
com certeza dizer!
