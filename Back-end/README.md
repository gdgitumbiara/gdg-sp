GDG-SP
=====

Código do back-end dos aplicativos do GDG-SP.

Caso você queira adaptá-lo para outro Meetup:

- Você precisará de um servidor com PHP e MySQL.
- Faça upload desses arquivos no seu servidor, e nos aplicativos onde você edita as informações do Meetup coloque a URL de onde você fez upload dos arquivos no "backend_url" ou "BackendUrl", mantendo a / no final.
- Edite o arquivo connect_db.php com as informações do seu banco de dados, no código comentado na linha 28 há um comando SQL para colocar o ID do Meetup e as chaves do aplicativo:
- Para as chaves da API do Meetup, [clique aqui](https://secure.meetup.com/meetup_api/oauth_consumers/) e escolha "Create New Consumer", no campo "Redirect URI" coloque o caminho do arquivo api/login.php, ficando dessa forma: http://{seu back-end}/api/login.php?meetupid={ID do seu meetup}
- Para as chaves do OneSignal, [faça uma conta](https://onesignal.com/) no site e crie um aplicativo no painel, após isso clique em "App Settings" na barra lateral e depois em Keys & IDs, para associar os aplicativos, leia a [documentação do OneSignal](https://documentation.onesignal.com).
- Para as chaves do WNS (usado no app para Windows 10), o OneSignal fornece um bom tutorial de como consegui-las, [clique aqui](https://documentation.onesignal.com/docs/windows-phone-client-sid-secret).
- No arquivo functions.php há uma variável $mapbox_token, esse token você consegue no [site do Mapbox](https://www.mapbox.com/studio/signup/), também há outra variável $qrcode, nela você coloca o valor padrão dos QR Codes gerados, a ID do usuário será adicionada ao final desse valor e gerará o QR Code.
- No arquivo functions.php também há um array $extramembers na função checkIsAdmin, nele você pode colocar o ID do Meetup de outros usuários para poderem enviar notificações sem ser um organizador do Meetup, o meu ID está como exemplo.

Para que a notificação de novos meetups seja automática, coloque um cron job direcionado para o arquivo notifications/cron.php de tempos em tempo, no mesmo arquivo, coloque a ID do seu meetup na variável $meetupids.

No back-end foi utilizado:

- [Leaflet](http://leafletjs.com)
- [Fonte Roboto](https://www.google.com/fonts/specimen/Roboto)
- [goQR.me](http://goqr.me/api/)