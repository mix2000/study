# Выполнение команды sudo без ввода пароля
Чтобы позволить пользователю выполнять команды sudo без ввода пароля, вам нужно добавить его в файл sudoers на вашем сервере. Вот как это сделать:

1. Войдите в систему на вашем сервере.
2. Откройте файл sudoers, выполнив команду sudo visudo. Эта команда открывает файл sudoers в текстовом редакторе и проверяет его на наличие ошибок при сохранении, что помогает предотвратить ситуацию, когда вы не сможете использовать sudo из-за некорректного файла sudoers.
3. Добавьте следующую строку в конец файла, заменив youruser на имя пользователя, которому вы хотите разрешить использование sudo без ввода пароля:

```
youruser ALL=(ALL:ALL) NOPASSWD: ALL
```
4. Сохраните изменения и закройте файл. В зависимости от используемого текстового редактора, это можно сделать разными способами. В редакторе nano вы можете нажать Ctrl+X, затем Y и Enter для сохранения и выхода.
После этого пользователь сможет выполнять команды sudo без ввода пароля.

Помните, что использование sudo без ввода пароля может быть опасно, так как если злоумышленники получат доступ к учетной записи пользователя, они смогут выполнить команды с повышенными привилегиями без ввода пароля.

### Нюансы

Если данная строка не работает, это может быть связано с различными причинами. Вот некоторые из них:

1. Проверьте, что строка "develop ALL=(ALL:ALL) NOPASSWD: ALL" добавлена в конец файла. Если другие директивы, которые также относятся к пользователю "develop", расположены после этой строки, они могут переопределять ее.
2. Проверьте, что вы сохранили файл sudoers после добавления строки.
3. Проверьте, что имя пользователя правильное и не имеет опечаток.
4. Убедитесь, что вы вышли из сессии и вошли снова, чтобы применить изменения.

Если все вышеперечисленное проверено и все равно не работает, попробуйте использовать следующую команду, которая предоставит все привилегии пользователю "develop":
```
develop ALL=NOPASSWD: ALL
```