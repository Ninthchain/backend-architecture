# Модуль core

В данном модуле, по моим предположениям, должны находится классы, описывающие функционал для работоспособности API.
К примеру, бизнес логике требуется распарсить XML файл, но в самом API такой функционал не приветствуется, и для этого будет создан XML-парсер, который в свою очередь будет имплементировать абстрактный интерфейс Parser. 
В итоге, сам сервис будет описывать взаимодействие функционала приложения, в то время, как ядро приложения будет являтся основынм фунционалом.
### Примечание!
Не надо изобретать велосипед, и писать всё с нуля. Писать собственный функционал ядра по возможности и при потребности.

```python

class ParserService:

    def get_current_coin_value(xml_parser: XMLpareser = Provide[Container.user_service]):
        try:
            binance_response = binanceapi.get("request url")
        except AbstractException:
            raise InternalProcessErrorException()
        if binance_response.status_code == 400:
            # В контроллере мы словим это исключение, и отправим нужный нам ответ клиенту
            raise BinanceApiAccessDeniedException()
        
        parsed_result = xml_parser.parse_coin(binance_response)

        return parsed_result
```