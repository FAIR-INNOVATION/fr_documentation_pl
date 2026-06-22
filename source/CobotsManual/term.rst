Terminologia
============

.. toctree:: 
	:maxdepth: 5


**Kategoria zatrzymania**:

- **Zatrzymanie kategorii 0**: Po odcięciu zasilania robota, robot natychmiast zatrzymuje działanie. Jest to zatrzymanie niekontrolowane. Ponieważ każdy staw jest hamowany z maksymalną prędkością, robot może odbiegać od zaprogramowanej ścieżki. Tego typu zatrzymania ochronnego można używać tylko po przekroczeniu granic oceny bezpieczeństwa lub gdy wystąpi błąd w części systemu sterowania odpowiedzialnej za ocenę bezpieczeństwa. Aby uzyskać więcej informacji, patrz EN ISO 13850:2008 lub IEC 60204-1:2006.
- **Zatrzymanie kategorii 1**: Robot zatrzymuje się, gdy zasilanie jest nadal dostarczane, a po osiągnięciu zatrzymania zasilanie jest odcinane. Jest to zatrzymanie kontrolowane, robot podąża zaprogramowaną ścieżką. Zasilanie jest odcinane po jednej sekundzie lub gdy robot całkowicie się zatrzyma. Aby uzyskać więcej informacji, patrz EN ISO 13850:2008 lub IEC 60204-1:2006.
- **Zatrzymanie kategorii 2**: Kontrolowane zatrzymanie przy zasilonym robocie. Robot zatrzymuje wszystkie ruchy w ciągu jednej sekundy. Sterowanie systemem oceny bezpieczeństwa umożliwia utrzymanie robota w pozycji zatrzymania. Aby uzyskać więcej informacji, patrz IEC 60204-1:2006.

**Pokrycie diagnostyczne (DC)**: Służy do pomiaru skuteczności diagnostyki wdrożonej w celu osiągnięcia ocenianego poziomu wydajności. Aby uzyskać więcej informacji, patrz EN ISO 13849-1:2008.

**Integrator**: Integrator to podmiot projektujący ostateczną instalację robota. Integrator jest odpowiedzialny za przeprowadzenie końcowej oceny ryzyka i musi zapewnić, że końcowa instalacja jest zgodna z lokalnymi przepisami i normami.

**Średni czas do uszkodzenia niebezpiecznego (MTTFd)**: Średni czas do uszkodzenia niebezpiecznego (MTTFd) to wartość obliczona i zmierzona w celu osiągnięcia ocenianego poziomu wydajności. Aby uzyskać więcej informacji, patrz EN ISO 13849-1:2008.

**Ocena ryzyka**: Ocena ryzyka to cały proces identyfikacji wszystkich zagrożeń i redukcji ryzyka do odpowiedniego poziomu. Ocena ryzyka powinna być udokumentowana. Więcej informacji można znaleźć w normie ISO 12100.

**Poziom wydajności**: Poziom wydajności (Performance Level, PL) to odrębny poziom, który opisuje zdolność poszczególnych części systemu sterowania związanych z bezpieczeństwem do wykonywania funkcji bezpieczeństwa w przewidywalnych warunkach. PLd to drugi najwyższy poziom wiarygodności, oznaczający, że funkcja bezpieczeństwa jest dość wiarygodna. Aby uzyskać więcej informacji, patrz EN ISO 13849-1:2008.

**Kołnierz przyłączeniowy**: Struktura służąca do podłączenia zewnętrznego narzędzia, powszechnie nazywana kołnierzem.

**Końcówka robota**: Ostatnia oś robota lub punkt środkowy kołnierza przyłączeniowego.

**Środkowy punkt narzędzia (TCP)**: Środkowy punkt narzędzia to charakterystyczny punkt narzędzia robota, punkt sterujący systemu robotycznego. Domyślnie znajduje się on w środku ostatniej osi ruchu lub kołnierza przyłączeniowego. Dla każdego narzędzia, jego środkowy punkt narzędzia zawiera przesunięcie i obrót określone względem środka wyjściowego kołnierza narzędzia. Współrzędne położenia X, Y, Z określają położenie środkowego punktu narzędzia, a RX, RY, RZ określają jego kierunek. Gdy wszystkie ich wartości wynoszą zero, środkowy punkt narzędzia pokrywa się ze środkiem kołnierza przyłączeniowego.

**Punkt położenia i orientacji narzędzia (TCF)**: W oparciu o środkowy punkt narzędzia TCP, odzwierciedla orientację układu współrzędnych narzędzia względem układu współrzędnych końcowego ogniwa.

**Podstawowy układ współrzędnych**: Początek podstawowego układu współrzędnych jest zwykle definiowany w punkcie środkowym między pierwszą osią robota a powierzchnią montażową. Oś X jest skierowana do przodu, w kierunku osiowym, a oś Y jest określana zgodnie z regułą prawej ręki.

**Światowy układ współrzędnych**: Stały układ współrzędnych zbudowany w komórce roboczej lub na stanowisku roboczym. Gdy jest tylko jeden robot, układ ten można uznać za pokrywający się z podstawowym układem współrzędnych. Gdy jest wiele robotów lub urządzeń zewnętrznych, światowy układ współrzędnych może stanowić unikalny układ odniesienia dla tych urządzeń. Pod warunkiem, że spełnia on wygodę kalibracji układów współrzędnych innych urządzeń, jego konkretne położenie może być określone dowolnie.

**Stawowy układ współrzędnych**: Stawowy układ współrzędnych to układ współrzędnych w stawach robota. W stawowym układzie współrzędnych każda oś robota może poruszać się niezależnie w kierunku dodatnim lub ujemnym w zakresie ograniczeń. Nadaje się do sytuacji, gdy wymagany jest ruch robota na dużą skalę bez konieczności zachowania orientacji TCP robota. Jednoosiowe punktowanie w trybie ręcznym robota jest wykonywane właśnie w stawowym układzie współrzędnych.

**Układ współrzędnych narzędzia**: Układ współrzędnych używany do określenia położenia środkowego punktu narzędzia i orientacji narzędzia. Gdy nie jest zdefiniowany, domyślny układ współrzędnych narzędzia znajduje się w środku kołnierza przyłączeniowego. Po zamontowaniu narzędzia TCP zmienia się, przesuwając się do środka końcówki narzędzia.

**Zewnętrzny układ współrzędnych narzędzia**: Układ współrzędnych używany do określenia położenia i orientacji narzędzia zamocowanego na zewnątrz robota.

**Oś rozszerzona**: Oprócz osi na samym korpusie robota, dodatkowe osie dodawane w celu spełnienia wymagań pracy. Oś rozszerzona obejmuje głównie takie typy, jak szyny przesuwne, stoły obrotowe i dodatkowe urządzenia serwonapędowe.

**Tryb ręczny**: W tym trybie wszystkie ruchy robota są ręcznie sterowane przez użytkownika, a zewnętrzne urządzenia zabezpieczające, takie jak kurtyny świetlne i drzwi bezpieczeństwa, nie działają, aby umożliwić bliskie debugowanie.

**Tryb automatyczny**: Ten tryb jest zwykle używany do uruchamiania programów nauczania robota, a zewnętrzne urządzenia zabezpieczające są włączone.

**Powtarzalność pozycjonowania**: Stopień zgodności pozycji i orientacji mierzonych w n powtórzeniach, gdy robot jest obsługiwany w tych samych warunkach i tą samą metodą.

**Panel operatorski**: Ręczna jednostka używana do programowania robota lub poruszania nim, połączona z systemem sterowania.