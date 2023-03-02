<script>
var ErreurHTML = '';
var formateForm = function (form) {
  let nomsASupprimer = [],
    f,
    r;
  if (form) {
    nomsASupprimer = Array.from(form.querySelectorAll('.nontransmis')).reduce(
      (a, c) => {
        a.push(c.name);
        return a;
      },
      []
    );
  }
  f = form ? new FormData(form) : new FormData();
  r = new FormData();
  for (var pair of f.entries()) {
    let n = pair[0],
      v = pair[1];
    if (n == 'datemaj') {
      r.set('datemaj', Date.now());
    } else if (v === 'on') {
      r.set(n, true);
    } else if (nomsASupprimer.indexOf(n) == -1 && v !== '') {
      r.set(n, v);
    }
  }
  return r;
};
export default {
  name: 'connexionAPI.service',
  methods: {
    async requete(url, form) {
      let f = formateForm(form),
        token = localStorage.getItem('token'),
        obj = {
          method: 'POST',
          body: f,
        };
      console.log('Token : ' + token);
      console.log('f : ' + f);
      if (token && !f.has('password')) {
        /*obj.headers = {
          'Content-Type': 'multipart/form-data',
          Authorization: 'Bearer ' + token,
        };*/
        f.set('##token', token);
      }
      return await fetch(url, obj)
        .then(async (reponse) => {
          if (!reponse.ok) {
            throw new Error(`HTTP erreur. status : ${reponse.status}`);
          }
          /*if (true) {
            //ErreurHTML = reponse.text();
            let r = reponse.body.tee();
            ErreurHTML = r[0].text();
          }
          return r[1].json();*/
          return reponse.json();
        })
        .catch((e) => {
          if (ErreurHTML) {
            document.body.append(ErreurHTML);
            ErreurHTML = '';
          }
          throw new Error('Attention : ' + e.message);
        });
    },
  },
};
</script>
