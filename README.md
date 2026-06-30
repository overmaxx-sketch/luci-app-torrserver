TorrServer for OpenWrt + LuCI Companion
(модифицированный workflow с полностью статичным ELF и OpenWrt‑пакетами)
Этот репозиторий собирает и публикует полностью статичные ARM64‑бинарники TorrServer, а также готовые ipk/apk‑пакеты для OpenWrt 21–25 и LuCI‑компаньон.

Здесь реализованы:
полная статическая линковка ELF
правильная упаковка под OpenWrt
отдельный LuCI‑пакет
поддержка двух ARM64‑архитектур OpenWrt
UPX‑вариант
сохранение UCI‑конфига при обновлении


Ключевые отличия от исходного workflow (важно)
✔ 1. Полностью статичный ELF ARM64‑бинарник
Оригинальный workflow  собирает pure Go static (без зависимостей, но не ELF‑static).
Здесь добавлено:

-extldflags '-static'

отсутствие BuildID

отсутствие NOTE‑секций

корректный ELF‑layout для musl/OpenWrt

Это даёт настоящий статичный ELF, который работает на OpenWrt/Flint2 без glibc и без ld-linux.

✔ 2. Сборка web‑assets и swagger включена в workflow
Оригинальный workflow собирает UI только для “standard” группы.
Здесь UI и swagger всегда собираются, чтобы бинарник был полностью функциональным.

