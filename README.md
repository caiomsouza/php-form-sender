# php-form-sender

Use the file send-emails-test.php to send e-mails using a Google SMTP Server.<BR>

More infos:<BR>
http://wiki.locaweb.com.br/pt-br/Envio_autenticado_na_revenda<BR>
http://wiki.locaweb.com.br/pt-br/Exemplos_de_Formulários_de_E-mail<BR>
http://wiki.locaweb.com.br/pt-br/Boas_práticas_de_envio_de_e-mail_por_seu_site<BR>


Important:<BR>
Login with your Google E-mail Account and go to:<BR>
At https://myaccount.google.com/u/2/security <BR>
Change:<BR>
Permitir aplicativos menos seguros: ATIVADA<BR>

###Code
```
<?php
 
require_once('class.phpmailer.php');
 
$mailer = new PHPMailer();
$mailer->IsSMTP();
$mailer->SMTPDebug = 1;
$mailer->Port = 587; //Indica a porta de conexão para a saída de e-mails. Utilize obrigatoriamente a porta 587.
 
$mailer->Host = 'smtp.gmail.com'; //Onde em 'servidor_de_saida' deve ser alterado por um dos hosts abaixo:
//Para cPanel: 'localhost';
//Para Plesk 11 / 11.5: 'smtp.dominio.com.br';
 
//Descomente a linha abaixo caso revenda seja 'Plesk 11.5 Linux'
$mailer->SMTPSecure = 'tls';
 
$mailer->SMTPAuth = true; //Define se haverá ou não autenticação no SMTP
$mailer->Username = 'it4biz@it4biz.com.br'; //Informe o e-mai o completo
$mailer->Password = 'YOUR_PASSWORD'; //Senha da caixa postal
$mailer->FromName = 'IT4biz Global - Site'; //Nome que será exibido para o destinatário
$mailer->From = 'it4biz@it4biz.com.br'; //Obrigatório ser a mesma caixa postal indicada em "username"
$mailer->AddAddress('info@it4biz.com.br'); //Destinatários
$mailer->Subject = 'E-mail sent by the IT4biz Global Site - '.date("H:i").'-'.date("d/m/Y");
$mailer->Body = 'Este é um teste realizado com o PHP Mailer';
if(!$mailer->Send())
{
echo "Mensagem nao enviada";
echo "Erro: " . $mailer->ErrorInfo; exit; }
print "E-mail enviado!";
 
?>

```



