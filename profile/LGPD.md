## :bookmark: **_LGPD_**


## Problema:
Quando se faz cadastro em qualquer aplicativo, os seus dados são adicionados a um banco e fica sob domínio da empresa em questão de modo que muitas empresas utilizam estes dados de modo inapropriado até mesmo quando o usuário já não faz mais uso do serviço ao qual se cadastrou, podendo trazer danos ao usuário e consequentemente fazendo-os se sentir desprotegidos quanto a privacidade e a liberdade sob seus dados.

## Proposta de solução:
Para solucionar estes casos, a LGPD foi criada.Definindo regras para a coleta, armazenamento, compartilhamento e a utilização de dados pessoais por empresas e órgãos públicos, possibilitando ao usuário uma maior segurança na hora de compartilhar seus dados
com as empresas. 
Uma das leis existentes para combater este uso indevido de dados é a Lei:XIV - eliminação: exclusão de dado ou de conjunto de dados armazenados em 
banco de dados, independentemente do procedimento empregado. 

Deste modo, em nosso App, o usuário é capaz de solicitar a exclusão de seus dados e ter a garantia que em até 15 dias seus dados serão eliminados de nossa base.

## Detalhes da implementação:

Ao iniciar o servidor é feito a chamada da função "Jobs", dentro desta função temos o Cron, trata-se de um gatilho que faz uma checagem no banco de dados a cada determinado tempo (neste caso, a checagem é feita a cada 5 minutos). 

Após este período de tempo o Cron chama a função “checkUser” que então realiza a checagem de usuários deletados de modo que sempre que um usuário solicita para ser removido de nosso aplicativo e ter seus dados excluídos de nossa base de dados, o mesmo é adicionado a uma tabela no banco de dados através de seu código identificador (id), então a função percorre a tabela de usuários deletados e a tabela de usuários ativos e compara os “id’s,” após a comparação, caso sejam encontrados identificadores iguais , o(s) mesmo(s) é/são deletado(s) da tabela de usuários ativos.

Caso seja feito um restore do banco de dados, não há problemas dos dados do usuário retornarem  a base, pois com o Cron fazendo esta checagem a cada período de tempo estipulado, garantimos que a tabela de usuários ativos se mantenha cada vez mais atualizada , trazendo assim mais conforto e segurança para o usuário.

https://user-images.githubusercontent.com/56592052/173958204-7aec2428-ee07-42cc-9cb2-26a7c0371a7d.mp4
