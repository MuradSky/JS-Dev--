# Фронтенд приколюхи

## Create React Component with dependent files
Чтобы создать компонент React со структурой папок, включая файл index.js, сам файл компонента (например, MyComponent.js) и связанный файл модуля SCSS, вы можете использовать скрипт NPM вместе с небольшим скриптом bash или скриптом Node.js.

Вот пример использования bash для создания структуры папок компонента React со всеми необходимыми файлами. Вы можете добавить этот скрипт в свой package.json или запустить его непосредственно в терминале.

1. Создайте файл под названием create-component.sh со следующим скриптом:
```bash
    #!/bin/bash

COMPONENT_NAME=$1
COMPONENT_DIR=./src/components/$COMPONENT_NAME

# Создание директории компонента
mkdir -p $COMPONENT_DIR

# Создание файла компонента
    cat <<EOL > $COMPONENT_DIR/$COMPONENT_NAME.js
    import React from 'react';
    import styles from './$COMPONENT_NAME.module.scss';
    
    const $COMPONENT_NAME = () => {
        return (
            <div className={styles.$COMPONENT_NAME}>
            <h1>$COMPONENT_NAME component</h1>
            </div>
        );
    };
    
    export default $COMPONENT_NAME;
    EOL
    
    # Создание SCSS-модуля
    touch $COMPONENT_DIR/$COMPONENT_NAME.module.scss
    
    # Создание index.js
    cat <<EOL > $COMPONENT_DIR/index.js
    export { default } from './$COMPONENT_NAME';
    EOL
    echo "Компонент $COMPONENT_NAME успешно создан!"
```
2. Сохраните его, выполнив команду (предполагается, что вы находитесь в корневом каталоге проекта):
```bash 
    nano create-component.sh
```
- Вставьте скрипт, затем нажмите CTRL + X, затем Y и ENTER, чтобы сохранить и выйти.
3. Дайте скрипту права на выполнение:
```bash 
    chmod +x create-component.sh
```
4. Запустите скрипт с именем вашего компонента:
```bash 
    ./create-component.sh MyComponent
```
- Это создаст структуру папок с вашим React-компонентом, SCSS-модулем и файлом index.js!
