# Padel

Licznik wyników do padla na Apple Watch. Jeden plik `index.html`, bez zależności.

- Live: https://czaja52.github.io/padel/
- Repo: https://github.com/czaja52/padel (publiczne, GitHub Pages z `main` /)
- Lokalnie: `~/projects/padel/index.html` (bez git, lokalny git blokowała niezaakceptowana licencja Xcode)

## Jak używać na zegarku

1. Wyślij sobie link w iMessage.
2. Na Watchu: Wiadomości, stuknij link.

## Co działa

- Wybór graczy (na sztywno: Dawid, Kamil, Kuba, Damian): stuknięcie przełącza MY / ONI / nikt. Start przy 1-2 graczach na drużynę.
- Punkty 0/15/30/40, gemy do 6 z przewagą 2, tiebreak przy 6:6 do 7, mecz do 2 setów.
- Złoty punkt domyślnie, przełącznik na przewagi.
- Cofnij (do 200 kroków), Nowa (przerwany mecz trafia do historii jako "przerwany").
- Historia sesji: godzina, składy, sety, zwycięzca, licznik wygranych na gracza. Wyczyść = nowa sesja.
- Zapis: `localStorage` (klucz `padel2`) + kopia w hashu URL.

## Znane ograniczenia

- Po OK na ekranie zwycięstwa nie da się cofnąć ostatniego punktu.
- Niezweryfikowane na zegarku: czy stan przetrwa zamknięcie Wiadomości.

## Deploy

Bez lokalnego gita, przez API:

```
sha=$(gh api repos/czaja52/padel/contents/index.html -q .sha)
gh api -X PUT repos/czaja52/padel/contents/index.html -f message="..." -f sha="$sha" -f content="$(base64 -i index.html)"
```

## Dalej (zaparkowane)

- Natywna apka watchOS (SwiftUI). Xcode jest w `/Applications/Xcode.app`, najpierw:
  `sudo xcode-select -s /Applications/Xcode.app && sudo xcodebuild -license accept`
- Instalacja przez darmowe Apple ID (certyfikat 7 dni). Alternatywne sklepy UE nie wchodzą w grę: dotyczą tylko iOS/iPadOS, wymagają notaryzacji i płatnego konta.
