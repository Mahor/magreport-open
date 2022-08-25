# Общие принципы архитектуры

## dataHub

dataHub - глобальный объект, доступ к которому может быть осуществлён из любого файла проекта. dataHub включает в себя объекты-контроллеры с функциями доступа к сервисам соответствующих контроллеров на сервере.

dataHub также содержит объект localCache (доступ можно получить через функцию getLocalCache). В объекте localCache сохраняются данные по различным сущностям, полученным с сервера. Ранее полученные данные могут быть использованы в любом месте приложения.

## store

store - глобальный объект для диспетчеризации событий. Может быть использован в любых местах приложения, в частности в action для диспетчеризации дочерних или отложенных событий.

## Main

В src/main/Main находятся непереиспользуемые компоненты, управляющие логикой различных частей приложения. Такие компоненты используют redux для хранения состояний и диспетчеризации событий.

## Переиспользуемые компоненты

Переиспользуемые компоненты (такие, как FolderContent) полностью управляются через передачу параметров от родительских компонентов (т.е. через props) и в большинстве случаев используют callback-функции для передачи событий для обработки родительским компонентам.

## DataLoader

Для загрузки данных в компоненты с сервера используется компонент DataLoader.
