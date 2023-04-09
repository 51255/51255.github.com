# 51255.github.com
<!DOCTYPE html>
<html>
  <head>
    <title>Convertisseur de date en date Hijri</title>
    <meta charset="utf-8" />
  </head>
  <body>
    <h1>Convertisseur de date en date Hijri</h1>
    <form>
      <label for="date_gregorienne">Entrez une date grégorienne :</label>
      <input type="date" id="date_gregorienne" name="date_gregorienne" />

      <button type="button" onclick="convertir()">Convertir</button>
    </form>

    <p id="resultat"></p>

    <script>
      function convertir() {
        // Récupération de la date grégorienne
        const date_gregorienne = new Date(
          document.getElementById("date_gregorienne").value
        );

        // Calcul de la date Hijri
        const timestamp =
          date_gregorienne.getTime() - date_gregorienne.getTimezoneOffset() * 60000;
        const date_hijri = new Date(timestamp);
        const annee_hijri = date_hijri.getFullYear();
        const mois_hijri = date_hijri.getMonth();
        const jour_hijri = date_hijri.getDate();

        // Affichage du résultat
        const jours_fr = [
          "Dimanche",
          "Lundi",
          "Mardi",
          "Mercredi",
          "Jeudi",
          "Vendredi",
          "Samedi",
        ];
        const mois_fr = [
          "janvier",
          "février",
          "mars",
          "avril",
          "mai",
          "juin",
          "juillet",
          "août",
          "septembre",
          "octobre",
          "novembre",
          "décembre",
        ];
        const jours_ar = [
          "الأحد",
          "الاثنين",
          "الثلاثاء",
          "الأربعاء",
          "الخميس",
          "الجمعة",
          "السبت",
        ];
        const mois_ar = [
          "جانفي",
          "فيفري",
          "مارس",
          "أفريل",
          "ماي",
          "جوان",
          "جويلية",
          "أوت",
          "سبتمبر",
          "أكتوبر",
          "نوفمبر",
          "ديسمبر",
        ];
        const mois_hijri_ar = [
          "محرم",
          "صفر",
          "ربيع الأول",
          "ربيع الثاني",
          "جمادى الأولى",
          "جمادى الثانية",
          "رجب",
          "شعبان",
          "رمضان",
          "شوال",
          "ذو القعدة",
          "ذو الحجة"
        ];
        const mois_hijri_fr = [
          "Mouharram",
          "Safar",
          "Rabi Al-Awwal",
          "Rabi Al-Thani",
          "Joumada Al-Awwal",
          "Joumada Al-Thani",
          "Rajab",
          "          "Sha'ban",
          "Ramadan",
          "Shawwal",
          "Dhu al-Qidah",
          "Dhu al-Hijjah"
        ];

        const jour_fr = jours_fr[date_gregorienne.getDay()];
        const mois_fr_label = mois_fr[date_gregorienne.getMonth()];
        const mois_ar_label = mois_ar[date_gregorienne.getMonth()];
        const mois_hijri_label = mois_hijri_ar[mois_hijri];

        const resultat_fr = `${jour_fr} ${date_gregorienne.getDate()} ${mois_fr_label} ${date_gregorienne.getFullYear()}`;
        const resultat_ar = `${jour_ar[date_gregorienne.getDay()]} ${date_gregorienne.getDate()} ${mois_ar_label} ${date_gregorienne.getFullYear()}`;
        const resultat_hijri = `${jour_hijri} ${mois_hijri_label} ${annee_hijri}`;

        document.getElementById("resultat").innerHTML = `
          <strong>Date grégorienne :</strong> ${resultat_fr} (${resultat_ar})<br />
          <strong>Date hijri :</strong> ${resultat_hijri}
        `;
      }
    </script>
  </body>
</html>
