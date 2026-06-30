# Это репозиторий для быстрого копирования моих любимых настроек конфигурации niri. 

## Секция input

Эти настройки добавляют поддержку русской раскладки клавиатуры, а также смену раскладки через комбинацию клавиш Shift+Alt

Также здесь настроен фокус окна при наведении мыши, но при условии что фокус окна не приведет перемещение на более чем 10% экрана(по крайней мере, примерно так я это понял)

И еще мышь будет "ускорения" чтоли, ну тобишь нормально будет без каких-либо добавок)))

Настройки тачпада я менять не стал, вроде бы все норм

```
input {
    keyboard {
        xkb {
            layout "us,ru"
            options "grp:alt_shift_toggle" 
        }

    }

    touchpad {
        // off
        tap
        // dwt
        // dwtp
        // drag false
        // drag-lock
        natural-scroll
        // accel-speed 0.2
        // accel-profile "flat"
        // scroll-method "two-finger"
        // disabled-on-external-mouse
    }

    mouse {
        // off
        // natural-scroll
        // accel-speed 0.2
	accel-profile "flat"
        // scroll-method "no-scroll"
    }
   focus-follows-mouse max-scroll-amount="10%"
}
```

## Секция output

Единственный параметр, который я добавил - это отключение "горячих-углов"


```
output "YOUR-MONITOR" {
	hot-corners {
		off
	}
}
```

## Секция автозапуска

Запуск xwayland-satellite - для x-вых приложений и программ, а также моя нокталия шелл

```
spawn-at-startup "xwayland-satellite" 
spawn-at-startup "qs" "-c" "noctalia-shell"
```

## Секция биндов

Бинды для эмодзи, лаунчера и буфера обмена с поддержкой скриншота.

P.S. Для работы нужны пакеты grim, slurp.
```
binds {
    Mod+Space { spawn-sh "qs -c noctalia-shell ipc call launcher toggle"; }

    Mod+P { spawn-sh "qs -c noctalia-shell ipc call launcher clipboard"; }
    Mod+E { spawn-sh "qs -c noctalia-shell ipc call launcher emoji"; }
 
 
    // Скриншот выделенной области в буфер обмена
    Mod+Shift+S { spawn "sh" "-c" "grim -g \"$(slurp -d)\" - | wl-copy -t image/png"; }
    // Скриншот всего экрана в буфер обмена
    Mod+S { spawn "sh" "-c" "grim - | wl-copy -t image/png"; }

```


вот как-то так))
