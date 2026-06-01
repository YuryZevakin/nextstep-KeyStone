# SONORE-REQ-001 — Многоязычный лендинг с информацией о школе

**Проект:** Sonore AI Transformation
**Статус:** Implemented (существующий функционал)
**Приоритет:** High

## Описание

Публичный сайт-визитка музыкальной школы Sonore Music Studio. Многоязычный (PL/EN).

## Структура сайта

### 1. Главная страница (`/`)
- Hero-секция: название "Sonore Music Studio", слоган "Sztuka dźwięku pod okiem mistrzów..."
- Подзаголовок: описание школы
- Блок "Dlaczego Sonore?" — Kadra akademicka, Więcej niż szkoła, Centrum Warszawy
- Блок "Kierunki" — 4 направления: Wokal, Fortepian, Perkusja, Teoria muzyki
- CTA-кнопка "Zapisz się na lekcję próbną"

### 2. О студии (`/about`)
- Философия: "Muzyka jako styl życia"
- Команда:
  - Tatiana Stepaniuk — założycielka, fortepian, teoria
  - Angelina Belanowicz — współzałożycielka, wokal
  - Alex Belanowicz — perkusja
- "Co nas wyróżnia": Indywidualne podejście, Atmosfera, Wydarzenia
- "Społeczność & Scena"

### 3. Контакты (`/contact`)
- Email: contact@sonoremusic.pl
- Адрес: ul. Pańska 96, lok. 63 (piętro 2), Warszawa
- Часы работы: Pon — Niedz: 09:00 - 21:00
- Social Media: Instagram, Facebook

### 4. Страницы услуг (`/services/`)
- `/services/vocal` — Nauka śpiewy (техника дыхания, эмиссия, интерпретация)
- `/services/piano` — Nauka gry na fortepianie (техника, музикальность, экзамены)
- `/services/drums` — Nauka gry na perkusji (техника, ритм, стили)
- `/services/theory` — Teoria muzyki, solfeż i harmonia

### 5. Форма записи ("Zapisz się")
- Поля: Imię i nazwisko, Email, Telefon, Wiadomość
- Валидация на клиенте
- Подтверждение отправки
- Обработка ошибок

### 6. Футер (все страницы)
- Меню: Start, O nas, Kontakt
- Услуги: все 4 направления
- Контакты: email, соцсети, адрес
- Копирайт

### 7. Мультиязычность
- PL (основной язык)
- EN (английская версия)
- Переключатель языка PL/EN в навигации

### 8. SEO
- Мета-теги (title, description) на каждой странице
- Open Graph (og:title, og:description, og:image, og:url)
- Twitter Card (summary_large_image)
- JSON-LD Schema: EducationalOrganization, LocalBusiness
- Канонические URL (rel=canonical)
- Hreflang (pl, en, x-default)
- Favicon
