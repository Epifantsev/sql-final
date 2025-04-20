Сервис **Parcel Tracker** для управления посылками на Go с использованием SQLite.

## Описание

Этот проект демонстрирует работу с базой данных SQLite через стандартный пакет `database/sql` и драйвер `modernc.org/sqlite`. Приложение позволяет:

- регистрировать новые посылки;
- просматривать все посылки конкретного клиента;
- менять адрес доставки (только если посылка ещё не отправлена);
- переводить посылку в следующий статус (`registered` → `sent` → `delivered`);
- удалять посылку (только если она в статусе `registered`).

## Структура проекта

- `main.go` — точка входа, демонстрация основных операций на примере.
- `parcel.go` — реализация `ParcelStore` с SQL‑операциями (Add, Get, GetByClient, SetStatus, SetAddress, Delete).
- `parcel_test.go` — юнит‑тесты для основных CRUD и бизнес‑правил.
- `tracker.db` — файл SQLite‑базы (данные).

## Технологии

- Go (1.18+)
- SQLite через драйвер `modernc.org/sqlite`
- `database/sql`
- Библиотеки для тестирования:  
  - `testing`  
  - `github.com/stretchr/testify/assert`  
  - `github.com/stretchr/testify/require`

## Установка и запуск

1. Клонируйте репозиторий:
   git clone https://github.com/Epifantsev/sql-final.git

2. Перейдите в папку проекта:
   cd sql-final
   
3. Убедитесь, что в директории есть файл tracker.db.

4. Запустите приложение:
   go run main.go
