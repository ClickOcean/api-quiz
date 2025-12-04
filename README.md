
## Список захардкоженных форм

Эти формы доступны для перестановки и переопределения текстов:

| Название формы | Описание |
|---------------|----------|
| `form-start` | Стартовая форма с приветствием |
| `form-who-attract` | Выбор пола партнера (кого ищу) |
| `form-you-are` | Выбор своего пола |
| `form-interest` | Выбор интересов |
| `form-birthday` | Ввод даты рождения |
| `form-name` | Ввод имени |
| `form-email-password` | Ввод email и пароля |
| `form-photo` | Загрузка фото (всегда последняя) |

## Типы шагов

### 1. Ссылка на существующую форму (только перемещение)

```json
{
  "name": "form-birthday"
}
```

### 2. Ссылка на существующую форму с переопределением текстов

```json
{
  "name": "form-you-are",
  "title": {
    "en-US": "New title for existing form",
    "es-ES": "Nuevo título"
  },
  "subtitle": {
    "en-US": "New subtitle"
  }
}
```

### 3. Новая динамическая форма (кнопки)

```json
{
  "name": "form-quiz-gender",
  "type": "button",
  "required": true,
  "title": {
    "en-US": "I am a..."
  },
  "subtitle": {
    "en-US": "Please select your gender"
  },
  "fieldName": "gender",
  "options": [
    {
      "value": "male",
      "label": { "en-US": "Man" }
    },
    {
      "value": "female",
      "label": { "en-US": "Woman" }
    }
  ]
}
```

### 4. Новая динамическая форма (одиночный выбор)

```json
{
  "name": "form-quiz-age-range",
  "type": "single",
  "required": true,
  "title": {
    "en-US": "What's your age range?"
  },
  "subtitle": {
    "en-US": "This helps us find compatible matches"
  },
  "submit": {
    "en-US": "Continue"
  },
  "fieldName": "age_range",
  "options": [
    {
      "value": "18-24",
      "label": { "en-US": "18-24" }
    },
    {
      "value": "25-34",
      "label": { "en-US": "25-34" }
    }
  ]
}
```

### 5. Новая динамическая форма (множественный выбор)

```json
{
  "name": "form-quiz-interests",
  "type": "multi",
  "required": false,
  "title": {
    "en-US": "What are your main interests?"
  },
  "subtitle": {
    "en-US": "Select all that apply"
  },
  "submit": {
    "en-US": "Continue"
  },
  "fieldName": "interests",
  "options": [
    {
      "value": "sports",
      "label": { "en-US": "Sports & Fitness" }
    },
    {
      "value": "music",
      "label": { "en-US": "Music" }
    }
  ]
}
```

## Типы форм

| Тип | Описание | Отображение |
|-----|----------|-------------|
| `button` | Выбор через кнопки | Автоматический submit при клике |
| `single` | Одиночный выбор | Radio buttons + кнопка Submit |
| `multi` | Множественный выбор | Checkboxes + кнопка Submit |

## Полный пример конфигурации

```json
{
  "quizSteps": [
    {
      "name": "form-you-are",
      "title": {
        "en-US": "Tell us about yourself"
      }
    },
    {
      "name": "form-quiz-gender",
      "type": "button",
      "required": true,
      "title": {
        "en-US": "I am a..."
      },
      "subtitle": {
        "en-US": "Please select your gender"
      },
      "fieldName": "gender",
      "options": [
        {
          "value": "male",
          "label": { "en-US": "Man" }
        },
        {
          "value": "female",
          "label": { "en-US": "Woman" }
        }
      ]
    },
    {
      "name": "form-who-attract"
    },
    {
      "name": "form-birthday"
    },
    {
      "name": "form-interest",
      "subtitle": {
        "en-US": "This helps us find perfect matches"
      }
    },
    {
      "name": "form-name"
    },
    {
      "name": "form-email-password"
    },
    {
      "name": "form-photo",
      "subtitle": {
        "en-US": "Upload your best photo"
      }
    }
  ]
}
```

## Правила и ограничения

1. ✅ **Форма `form-photo` всегда последняя** - система автоматически поместит её в конец, независимо от позиции в JSON
2. ✅ **Локализация** - все тексты поддерживают мультиязычность через объекты с кодами языков
3. ✅ **Существующие формы** - можно переставлять и изменять только `title` и `subtitle`
4. ✅ **Новые формы** - требуют полную конфигурацию с `type`, `fieldName`, `options`
5. ⚠️ **Форма `form-start`** - не рекомендуется перемещать, так как она служит точкой вставки