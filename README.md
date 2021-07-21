# chirpstack2zabbix
ChirpStack http integration -> this code -> the zabbix server

## Setup
0. clone into `/somewhere/` and `cd /somewhere/`
0. run `composer install`
0. copy+edit `config/config.php.sample` into `config/config.php`
0. Sample setup for apache:
   ```
    Alias /c2z/ "/somewhere/"
    <Directory "/somewhere/">
      Require all granted
      Require local
    </Directory>
   ```
0. reload apache
0. chirpstack config
  * Go to `Applications/$app_name/Integrations/http`
  * Payload marshaller : JSON
  * Endpoints: `http://localhost:/c2z/?debug`
0. zabbix config
  * item type : zabbix trapper
  * key : chripstack.$app_name.$device_name.$key (The payload must be decoded by a JavaScript function in the device proflie).
0. test
0. remove `?debug` from the endoinps url.

