## ‎連接中的多串流

與 SCTP、SSH 和 HTTP/2 相似，QUIC 在物理連接內具有獨立的邏輯流。 許多並行流可以透過單個連接同時傳輸資料，而不會影響其他流。

連接兩個端點之間的協商設置是類似於 TCP 連接的工作方式。
QUIC 連接建立到 UDP 端口和 IP 地址，但是一旦建立，該連接就由其 "連接ID"（ connection ID ）關聯。

通過已建立的連接，任何一方都可以創建流並將資料發送到另一端。
單一串流的傳輸是可靠、有序的，但不同的串流間可能會有無序傳送。

QUIC 可對連接和串流分別進行流量控制（ flow control ）。

進一步細節請參考 [連接](quic-connections.md) 和 [QUIC串流](quic-streams.md)。