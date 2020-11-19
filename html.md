# HTML style guidelines

## General

Follow the [general guidelines](general.md).

Jāizmanto [derīgs HTML](https://validator.w3.org/)

Jānorāda dokumenta tips (ieteicams lietot HTML5) un kodējums. Vēlams arī
skatlauks.
```html
<!doctype html>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Jāizvēlas elementi atbilstoši to semantikai. Piemēram, `table` tabulām, 
`header` galvenei utt.

Pēc iespējas jāizmanto `HTTPS` protokols, norādot to kā shēmu vietrādī.
Jāizvairās no bezshēmas vietrāžiem.

Ja nav īpašu nolūku, kas liek rīkoties citādi, stils un skripti jāizdala 
atsevišķās datnēs. It īpaši, ja tiek atkārtoti izmantoti vairākiem skatiem.

## Komentāri

Komentārus no komentēšanas notācijas jāatdala ar vienu atstarpi katrā pusē.
```html
<!-- Komentārs -->
```

Vairāku rindu komentāri jāatver un jāaizver atsevišķās rindās ar vienādu atkāpi. Komentāra saturam jābūt vismaz vienu līmeni dziļākai atkāpei.
```html
<!--
	Komentāra pirmā rinda;
	komentāra otrā rinda.
-->
```

## Nosaukumu pieraksts

Elementu un atribūtu nosaukumiem lietojami tikai mazie burti. Atribūtu vērtības
var likt pēdiņās vai atstāt brīvas. Atribūtu nosaukumi un vērtības jāatdala
tikai ar vienādības zīmi, nelietojot papildus atstarpes.
```html
<span class=sporty>Jumpy</span>
<span class="sporty athletic">Jumpy</span>
```

Būla atribūtiem nav jānorāda nekāda vērtība
```html
<button disabled>Don't!</button>
```
 
## Vērtību kapitalizācija

Klases, identifikatorus un atsevišķus citus atribūtus HTML standarts ļauj
rakstīt jebkādus un gandrīz jebkādā formā. Rakstām pilnus un aprakstošus
nosaukumus, kas atspoguļo vērtības nozīmi nevis tās saīsinājumu vai patvaļīgu
atslēgas vārdu.

Vēlams izmantot vērtības, kas saskan ar citur (*PHP*, *JavaScriptā*, datubāzē,
utt.) izmantotajām. Ja lauks datubāzē ir `user_id`, tad
```html
<input name=user_id class=user_id >
```
ir optimālais variants. Ja šādu konsisttences apstākļu nav, kā pamatvariantu
izmantojam tradicionālo *kebabu-rakstu*. 

## Elementu aizvēršana
Ne-tukšo elementu birkas jāraksta bez atstarpes pēc atverošā vai pirms
aizverošā knābja.
```html
<a href="#hund">HUND!</a>
```

Tukšie elementi jānoslēdz ar atstarpi pirms aizverošā knābja. Drīkst aizvietot
`>` ar `/>`.
```html
<!-- Ieteicams -->
<input name="email" >

<!-- Pieļaujams sadarbībai ar XML parsētājiem -->
<input name="email" />
```

## Neobligātās atzīmes
Elementiem, [kas tiek izveidoti un noslēgti automātiski](https://html.spec.whatwg.org/multipage/syntax.html#syntax-tag-omission), 
vēlams izmantot tikai obligāti nepieciešamos tagus.
```html
<!doctype html>
<html lang="lv">
<title>Paraugs</title>
<p>Ir nepieciešama atverošā html atzīme, jo tai jānorāda atribūts.
<p>Nav nepieciešams aizvērt html.
<p>Nav nepieciešams norādīt head un body.
```

Elementiem, kam aizverošā atzīme ir neobligāta, to jāizlaiž, ja birkas tiek
rakstītas vienā rindā ar elementa saturu.
```html
<ul>
	<li>Pirmais elements
	<li>Otrais elements
	<li>
		Lietot neobligātu aizverošo birku ļauts, kad tā izvietota atsevišķā rindā
	</li>
</ul>
```

## Neobligātie atribūti

Atribūts `type` nav jāizmanto, ja vien nav nepieciešams.
```html
<link rel="stylesheet" src="css/main.css" >
<script src="js/main.js"></script>
```

## Elementu strukturēšana

Elementam, kas atrodas citā elementā (sencī), jāatrodas atsevišķā rindā un tā
atkāpei jābūt par vienu līmeni dziļākai nekā sencim. Elementam, kura atverošā
un aizverošā atzīme atrodas dažādās rindās, šīm atzīmēm jābūt vienādai atkāpei.
```html
<section>
	<div>
		<input name=email >
	</div>
</section>
```

Izņēmums ir teksta elementi. Vienas rindas teksta elementiem jātiek atvērtiem un aizvērtiem tajā pašā rindā.
```html
<span class=sporty>Jumpy</span>
```

Vairāku rindu teksta elementiem pieļaujams gan viens, gan otrs risinājums.
 
Izņēmums ir arī augstākā līmeņa elementu saturs. `html` un `body` elementu
saturam papildus atkāpe nepienākas. Tā tiek darīts, lai dokuments būtu mazliet
tuvāk kreisajai malai.
```html
<html>
<head>
	<title>Important</title>
</head>
<body>
<header>
	<div>
		<h1>Important!</h1>
		<nav>
			<ul>
				<li>Home
				<li>Contacts
			</ul>
		</nav>
	</div>
</header>         
<footer>
	<p>All rights reserved.
</footer>
</body>
</html>
```

Elementi, kas atrodas tekstā, nav jāizdala atsevišķā rindā.
```html
This is a <em>correcty</em> example.
```

Izņēmuma gadījumā elementus var strukturēt citādi, ja tas uzlabo lasāmību.
```html
<table>
	<tr><th>Klients    <th>Pilsēta    <th>Pirkumi
	<tr><td>Ainis      <td>Dobele     <td>5
	<tr><td>Malda      <td>Saldus     <td>3
</table>
```

Ja viens otrā ietilpst viena tipa elementi, ārējā elementa aizverošā birka
jāpapildina ar komentāru, norādot, kas tiek aizvērts. Komentārs jāsāk ar `/ ` 
un jāizmanto `id`, ja ir. Ja nav tad `class`, `name` vai patvaļīga vērtība. 
Pierakstam jāizmanto CSS selektoru sintakse.
```html
<div id=main-wrapper>
	<div class=upper-block>
		<div class=content>
		</div>
	</div> <!-- / .upper-block -->
</div> <!-- / #main-wrapper -->
```

Var izmantot komentāru ar sekojošu tukšu rindu, lai noslēgtu daļu koda.
```html
<section>
	<div></div>
</section>
<section>
	<div></div>
</section>
<!-- / sadaļu bloks -->

<form>
</form>
```

## Atribūtu strukturēšana
Ja elementam ir viens atribūts, rakstām elementu vienā rindā.
```html
<input name=email >
```

Ja elementam ir daudzi atribūti, rakstām katru atribūtu atsevišķā rindā.
Aizverošais knābis jāizvieto pēdējā atribūta rindā pēc atstarpes.
```html
<input
	type=email
	name=email
	placeholder="Your e-mail"
	class=invisible-input
	id=email-input >
```

Ja elementam ir divi vai trīs atribūti un to iespējams pierakstīt vienā rindā,
dalīšana vai nedalīšana rindās ir pēc autora novērtējuma. Tas attiecas arī uz
saturu izdalīšanu atsevišķā rindā.
```html
<input type=checkbox checked >

<input
	class="free-input has-error"
	placeholder="Please don't touch this input" >

<!--
	Šie ir paraugi atsevišķām situācijām.
	Viena saraksta ietvaros jāievēro konsistenti principi.
	Izņēmums var būt kāds speciāls (piem. pirmais) elements.
-->
<option value="1">Tomato
 
<option value="fruit" selected>
	Tomato
</option>
```

Sadalot atribūtu vairākās rindās, tā saturam pienākas dubulta atkāpe:
```html
<option
	value="fruit"
	data-id="358"
	data-img="fruit_salad.png"
	selected >
		Tomato
</option>
```

## Dokumenta strukturēšana

### Head (SEO, meta tagi u.c.)
Iekļaujamie objekti sagrupēti pa lielākiem punktiem. Starp šo tagu grupām
jāliek tukša rinda. Iekļaujamo tagu saraksts ir šāds:

1. html un lokāle
    1. doctype
    2. html lang=".."  -  ja norāda lokāli headeros, šo tagu var izlaist
    3. meta charset
2. Saturs
    1. title
    2. meta description
    3. link canonical - neobligāts
    4. meta robots - pēc vajadzības
    5. meta mobile web app capable - pēc vajadzības
    6. meta keywords, meta author - nevēlami
3. OpenGraph - neobligāts
    1. og:title
    2. og:site_name
    3. og:description
    4. og:url - ja norāda link canonical
    5. og:type
    6. og:locale
    7. og:locale:alternate
    8. og:image - ja ir
    9. citi OG atbilstoši saturam
4. Twitter - neobligāts
	1. twitter:card
	2. citi twitter, ja atšķiras no OG
5. Asseti un vizuālais
    1. favicon tagi
	2. viewport
    3. vietnes CSS
    4. vietnes JS - tikai, ja nevar novietot body beigās
6. Citi tagi, piem meta csrf-token
7. Lapas asseti
    1. lapas CSS
    2. lapas JS, ja jānovieto sākumā

Paraugs:
```html
<!doctype html>
<html lang="{{App::getLocale()}}">
<meta charset="UTF-8" />

<!-- Content meta -->
<title>{{$content->title}} | The Site</title>
<meta name="description" content="{{strip_tags($content->introduction ?? '')}}{{strip_tags($content->intro ?? '')}}">
<link rel="canonical" href="{{$content->getUrl()}}">

<!-- OpenGraph -->
<meta property="og:title" content="{{$content->title}}" >
<meta property="og:site_name" content="The Site" >
<meta property="og:description" content="{{strip_tags($content->introduction ?? '')}}{{strip_tags($content->intro ?? '')}}" >
<meta property="og:url" content="{{$content->getUrl()}}" >
<meta property="og:type" content="{{'App\Article' == get_class($content) ? 'article' : 'website'}}" >
@foreach (LaravelLocalization::getSupportedLocales() as $lc => $locale)
@if ($lc == App::getLocale())
<meta property="og:locale" content="{{$locale['regional']}}" >
@else
<meta property="og:locale:alternate" content="{{$locale['regional']}}" >
@endif
@endforeach
@if ($content->images->first() ?? false)
<meta property="og:image" content="{{asset($content->images->first()->path)}}" >
@endif

<!-- Twitter -->
<meta name="twitter:card" content="summary" >

<!-- Assets -->
<link rel="apple-touch-icon" sizes="180x180" href="{{asset('img/fav/apple-touch-icon.png')}}">
<link rel="icon" type="image/png" sizes="32x32" href="{{asset('img/fav/favicon-32x32.png')}}">
<link rel="icon" type="image/png" sizes="16x16" href="{{asset('img/fav/favicon-16x16.png')}}">
<link rel="manifest" href="{{asset('site.webmanifest')}}">
<link rel="mask-icon" href="{{asset('safari-pinned-tab.svg')}}" color="#5bbad5">
<meta name="msapplication-TileColor" content="#ffffff">
<meta name="theme-color" content="#ffffff">

<meta name="viewport" content="width=device-width,initial-scale=1">
<link href="https://fonts.googleapis.com/css?family=Open+Sans:400,600,700,800&amp;subset=cyrillic,latin-ext" rel="stylesheet">
<link rel="stylesheet" href="{{asset('css/fontawesome-all.min.css')}}">
<link rel="stylesheet" href="{{mix('css/main.css')}}">

<meta name="csrf-token" content="{{csrf_token()}}">
@stack('head')
@yield('head')
```
