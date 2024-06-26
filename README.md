## Data Science
В этом репозитории собраны работы по парсингу и обработке месячных показателей ИПЦ России, полученных с официальной витрины данных Росстата https://showdata.gks.ru/finder/. Данный ресурс реже находится оффлай в сравнении с ЕМИСС (https://fedstat.ru) и более производителен в сравнении с BI-порталом (http://bi.gks.ru/biportal/contourbi.jsp?allsol=1&solution=Dashboard). Сознательно не использовались годовые приросты, так как они являются производными от месячных. 


#### Содержание: / Content:

- **Parser.ipynb**
  - Здесь происходит парсинг витрины данных и получение выгрузки pivot_df.csv
  - Сайт имеет особенность SSL-сертификата, чтобы получать данные в запросе get необходимо отключать проверку безопасности
  - Из-за переполнения SQL запроса к серверу отсуствует возможность сразу получить всю историю наблюдений с 2002 года. Чтобы избежать этой ошибки данные выгружаются помесячно.
  - Настройки фильтров (даты, компоненты ИПЦ, регионы) вшиты в url для экономии времени. В будущем можно создать полноценные функциональные словари и делать специфические запросы (срезы дат, регионов и компонентов). Текущий парсер выгружает все месячные приросты по всем компонентам ИПЦ в целом по РФ
- **Prophet.ipynb**  
  - Модель пространства состояний с хорошей производительностью RMSE: 0.2981
- **ARIMA.ipynb**  
  - Простая авторегрессионная модель RMSE: 0.3144
- **Разведывательный анализ данных / Data_reasearch**
  - Исследование выгруженных данных на предмет пропущенных значений, нормальности и базовых статистических показателей
