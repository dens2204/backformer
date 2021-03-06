#Backformer 2.0

Ajax форма обратной связи, легко интегрируемая абсолютно в любую CMS.

##Достоинства
* Возможность отправки через ajax любых форм.
* Поддержка капчи.
* Поддержка прикрепления к письму нескольких файлов.
* Защита от спама, CSRF.
* Поддержка работы с несколькими формами на одной странице.
* Поддержка локализаций.
* Поддержка всплывающих окон Fancybox.


## Как подключить

###1. Подключить скрипты в указанной последовательности

Для работы формы потребуется jquery:

    <script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
    
Опционально, [галерея fancyBox](https://github.com/fancyapps/fancyBox) для модальных окон:

    <!-- Add fancyBox main JS and CSS files -->
    <script type="text/javascript" src="/backformer/core/components/fancybox_2.1.5/source/jquery.fancybox.pack.js">
    </script>
    <link rel="stylesheet" type="text/css" href="/backformer/core/components/fancybox_2.1.5/source/jquery.fancybox.css" media="screen" />
    <!-- // end add fancyBox -->

Плагин jquery для отправки форм [jquery.form.js](https://github.com/malsup/form):

    <!-- ajax jquery form -->
    <script src="/backformer/core/components/jquery_form/jquery.form.min.js"></script>
    <!-- // end ajax jquery form -->

Сам скрипт:

    <!-- back form -->
    <link href="/backformer/core/themes/default.css" type="text/css" rel="stylesheet" />
    <script src="/backformer/core/components/backformer.js"></script>
    <!-- // end back form -->

####Параметры

Для подключения достаточно навесить на форму атрибут **data-bf-config=""** и передать ему название конфигурации.

По умолчанию, при пустом вызове конфигурации, будет браться из папки **/configs/default**. Можно создать сколько угодно конфигураций, просто копируя эту папку с другим названием.  

####Что внутри

* config.php - конфигурационный файл.
* report.html - шаблон отправки на почту. В качестве шаблона для полей используется конструкция **[+название_поля+]** 
* form.html - форма в всплывающем окне fancybox.

###2. Пример вызова формы

    <div class="bf-content-inline">
        <div class="bf-header">
            Форма отправки сообщения!
        </div>
        <form data-bf-config="" action="" method="post">
            <div class="bf-row">
                <label>Имя:</label>
                <input required="required" name="name" placeholder="Обязательное поле" type="text" value="" />
            </div>
            <div class="bf-row">
                <label>Телефон:</label>
                <input required="required" name="phone" placeholder="Обязательное поле" type="text" value="" />
            </div>
            <div class="bf-row">
                <label>Комментарий:</label>
                <textarea cols="40" rows="10" name="comment"></textarea>
            </div>
            <div class="bf-row">
                <label>Прикрепить файлы:</label>
                <input multiple="multiple" name="upload_file[]" type="file" />
            </div>
            <div class="bf-row">
                <div class="bf-info-img">
                    <img title="Обновить картинку" class="bf-img-capcha" src="/backformer/core/model/kcaptcha/index.php" alt="" />
                </div>
                <input class="capcha" name="capcha" placeholder="Код с картинки" type="text" value="" />
            </div>
            <div class="bf-submit">
                <input class="bf-button" name="submit" type="submit" value="Отправить" />
            </div>
        </form>
    </div>



###3. Пример вывоза всплывающего окна Fancybox

Для создания всплывающего окна достаточно присвоить атрибут **data-bf-init="popup"** ссылке или кнопке. 

	<a data-bf-init="popup" href="#">Модальное окно</a>

Работает пока только с **/configs/default**.
 
