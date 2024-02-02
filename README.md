<div style = "font-family: 'Open Sans', sans-serif; font-size: 16px">

# ModuleSensor
<div style = "color: #555">
    <p align="center">
    <img src="./res/logo.png" width="400" title="hover text">
    </p>
</div>

## Лицензия
////

### Описание
<div style = "color: #555">

SensorManager - системная служба, ключевой компонент фреймворка EcoLight, разработанный для обеспечения взаимодействия между серверным уровнем, к которому могут относиться, к примеру, MQTT-брокер или Node-RED сервер, и полевым уровнем, который включает в себя все инициализированные на платформе датчики и актуаторы. Данная служба предоставляет следующие функции:
- Ведение реестра датчиков и актуаторов. Все программные модули датчиков/актуаторов, реализованные в соответствии с архитектурой [ModuleSensor](https://github.com/Konkery/ModuleSensor)/[ModuleActuator](https://github.com/Konkery/ModuleActuator), при инициализации автоматически регистрируются в SensorManager. Таким образом служба обеспечивает доступ ко всему измерительно-исполняющему слою платформы через единый интерфейс, с которым можно взаимодействовать как со стороны сервера, так и в рамках контроллера;
- Периодический сбор показаний с измерительных каналов. Sensor Manager содержит механизм, который по запросу внешнего агнета запускает циклический сбор данных со всех измерительных каналов зарегистрированных на платформе датчиков. При этом данные, которые не обновились с момента последней итерации, пропускаются. Собранные данные далее поступают на сервер посредством установленных каналов связи;
- Сбор и передача метаданных метаданных от всех датчиков и актуаторов. Предоставляет целостную информацию о каждом измерительном/исполняющем устройстве на платформе EcoLight;
- Прием и перенаправление команд. Принимает команды от сервера и направляет их соответствующим датчикам и актуаторам. Обеспечивает возможность контролировать процессы полевого уровня платформы с сервера;

<div align='left'>
    <img src="./res/diagram v02 no-color.png" alt="Image not found">
</div>

#### Взаимодействие с прокси-службами

Диаграмма выше демонстрирует, что Sensor Manager не взаимодействует с клиент-серверными службами напрямую. Вместо этого он ведет двунаправленный обмен сообщениями с их прокси-службами. 

<div align='left'>
    <img src="./res/diagram data-tx.png" alt="Image not found">
</div>

</div>

### Поля
<div style = "color: #555">

- <mark style="background-color: lightblue">_Devices</mark> - массив, хранящий ссылки на объекты инициализированных датчиков и актуаторов.
</div>

### Аксессоры
<div style = "color: #555">

- <mark style="background-color: lightblue">Sensors</mark> - геттер, возвращающий массив со ссылками только на датчики;
- <mark style="background-color: lightblue">Actuators</mark> - геттер, возвращающий массив со ссылками на актуаторы.
</div>

### События
<div style = "color: #555">

- <mark style="background-color: lightblue">sensor-start-polling</mark> - запрос на запуск циклического опроса датчиков и пакетной рассылки собранных показаний;
- <mark style="background-color: lightblue">sensor-stop-polling</mark> - прекращение опроса;
- <mark style="background-color: lightblue">sensor-get-info</mark> - запрос на сбор метаданных сенсоров и актуаторов;
- <mark style="background-color: lightblue">sensor-write</mark> - перенаправление команды актуатору;
- <mark style="background-color: lightblue">new-device</mark> - регистрация нового устройства (датчика/актуатора).

</div>

### Методы
<div style = "color: #555">

<div style = "color: #555">

- <mark style="background-color: lightblue">AddDevice(device)</mark> - добавляет устройство в реестр;
- <mark style="background-color: lightblue">GetDevice(id)</mark> - Возвращает устройство с соответствующим id;
- <mark style="background-color: lightblue">GetDeviceChannel(chId)</mark> - возвращает канал устройства по его id;
- <mark style="background-color: lightblue">StartPolling(_freq)</mark> - запускает периодическое считывание данных с сенсоров;
- <mark style="background-color: lightblue">StopPolling()</mark> - прекращает периодический опрос датчиков;
- <mark style="background-color: lightblue">GetSensorsInfo()</mark> - собирает и возвращает метаданные с зарегистрированных сенсоров и актуаторов;
- <mark style="background-color: lightblue">StopPolling()</mark> - прекращает периодический опрос датчиков;
- <mark style="background-color: lightblue">SendData(dataPackage)</mark> - прекращает периодический опрос датчиков;
- <mark style="background-color: lightblue">ExecuteCom(arg)</mark> - перенаправляет команду от внешнего агента на исполнение.

</div>

</div>

### Примеры
<div style = "color: #555">

```js

```

#### Результат выполнения:

<div align='left'>
    <img src="./res/example-1.png" alt="Image not found">
</div>

</div>

### Зависимости
<div style = "color: #555">

- <mark style="background-color: lightblue">[ClassAppError](https://github.com/Konkery/ModuleAppError/blob/main/README.md)</mark>
</div>

</div>
    