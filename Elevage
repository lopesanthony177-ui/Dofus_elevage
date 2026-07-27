from kivy.app import App
from kivy.uix.screenmanager import ScreenManager, Screen
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.label import Label
from kivy.uix.button import Button
from kivy.uix.spinner import Spinner
from kivy.uix.scrollview import ScrollView
from kivy.utils import get_color_from_hex

CROISEMENTS_DRAGODINDES = {
    "Amande Dorée": ("Amande", "Dorée"), "Amande Rousse": ("Amande", "Rousse"), "Dorée Rousse": ("Dorée", "Rousse"),
    "Ebene": ("Amande Dorée", "Dorée Rousse"), "Indigo": ("Amande Dorée", "Amande Rousse"),
    "Ebene Rousse": ("Ebene", "Rousse"), "Amande Ebene": ("Amande", "Ebene"), "Amande Indigo": ("Amande", "Indigo"),
    "Dorée Ebene": ("Dorée", "Ebene"), "Dorée Indigo": ("Dorée", "Indigo"), "Ebene Indigo": ("Ebene", "Indigo"),
    "Indigo Rousse": ("Indigo", "Rousse"), "Pourpre": ("Amande Rousse", "Ebene Indigo"), "Orchidée": ("Dorée Rousse", "Ebene Indigo"),
    "Amande Orchidée": ("Amande", "Orchidée"), "Amande Pourpre": ("Amande", "Pourpre"), "Dorée Orchidée": ("Dorée", "Orchidée"),
    "Dorée Pourpre": ("Dorée", "Pourpre"), "Ebene Orchidée": ("Ebene", "Orchidée"), "Ebene Pourpre": ("Ebene", "Pourpre"),
    "Indigo Orchidée": ("Indigo", "Orchidée"), "Indigo Pourpre": ("Indigo", "Pourpre"), "Orchidée Rousse": ("Orchidée", "Rousse"),
    "Pourpre Rousse": ("Pourpre", "Rousse"), "Orchidée Pourpre": ("Orchidée", "Pourpre"),
    "Turquoise": ("Ebene Orchidée", "Orchidée Pourpre"), "Ivoire": ("Indigo Pourpre", "Orchidée Pourpre"),
    "Ebene Ivoire": ("Ebene", "Ivoire"), "Ivoire Rousse": ("Ivoire", "Rousse"), "Amande Ivoire": ("Amande", "Ivoire"),
    "Amande Turquoise": ("Amande", "Turquoise"), "Dorée Ivoire": ("Dorée", "Ivoire"), "Dorée Turquoise": ("Dorée", "Turquoise"),
    "Ebene Turquoise": ("Ebene", "Turquoise"), "Indigo Ivoire": ("Indigo", "Ivoire"), "Indigo Turquoise": ("Indigo", "Turquoise"),
    "Ivoire Turquoise": ("Ivoire", "Turquoise"), "Ivoire Orchidée": ("Ivoire", "Orchidée"), "Ivoire Pourpre": ("Ivoire", "Pourpre"),
    "Turquoise Rousse": ("Turquoise", "Rousse"), "Turquoise Orchidée": ("Turquoise", "Orchidée"), "Turquoise Pourpre": ("Turquoise", "Pourpre"),
    "Emeraude": ("Ivoire Turquoise", "Ivoire Pourpre"), "Prune": ("Ivoire Turquoise", "Turquoise Orchidée"),
    "Amande Emeraude": ("Amande", "Emeraude"), "Dorée Emeraude": ("Dorée", "Emeraude"), "Ebene Emeraude": ("Ebene", "Emeraude"),
    "Emeraude Indigo": ("Emeraude", "Indigo"), "Emeraude Ivoire": ("Emeraude", "Ivoire"), "Emeraude Rousse": ("Emeraude", "Rousse"),
    "Emeraude Turquoise": ("Emeraude", "Turquoise"), "Emeraude Orchidée": ("Emeraude", "Orchidée"), "Emeraude Pourpre": ("Emeraude", "Pourpre"),
    "Prune Amande": ("Prune", "Amande"), "Prune Dorée": ("Prune", "Dorée"), "Prune Ebene": ("Prune", "Ebene"),
    "Prune Emeraude": ("Prune", "Emeraude"), "Prune Indigo": ("Prune", "Indigo"), "Prune Ivoire": ("Prune", "Ivoire"),
    "Prune Rousse": ("Prune", "Rousse"), "Prune Turquoise": ("Prune", "Turquoise"), "Prune Orchidée": ("Prune", "Orchidée"),
    "Prune Pourpre": ("Prune", "Pourpre")
}

CROISEMENTS_VOLKORNES = {
    "Pourpre Orchidée": ("Pourpre", "Orchidée"), "Pourpre Indigo": ("Pourpre", "Indigo"), "Pourpre Ebene": ("Pourpre", "Ebene"),
    "Orchidée Indigo": ("Orchidée", "Indigo"), "Orchidée Ebene": ("Orchidée", "Ebene"), "Indigo Ebene": ("Indigo", "Ebene"),
    "Roux": ("Pourpre Orchidée", "Pourpre Indigo"), "Amande": ("Pourpre Ebene", "Orchidée Ebene"),
    "Ivoire": ("Pourpre Indigo", "Indigo Ebene"), "Turquoise": ("Pourpre Orchidée", "Orchidée Ebene"),
    "Amande Pourpre": ("Amande", "Pourpre"), "Amande Indigo": ("Amande", "Indigo"), "Amande Ebene": ("Amande", "Ebene"),
    "Amande Roux": ("Amande", "Roux"), "Amande Ivoire": ("Amande", "Ivoire"), "Amande Turquoise": ("Amande", "Turquoise"),
    "Roux Pourpre": ("Roux", "Pourpre"), "Roux Orchidée": ("Roux", "Orchidée"), "Roux Indigo": ("Roux", "Indigo"),
    "Roux Ebene": ("Roux", "Ebene"), "Roux Ivoire": ("Roux", "Ivoire"), "Roux Turquoise": ("Roux", "Turquoise"),
    "Ivoire Pourpre": ("Ivoire", "Pourpre"), "Ivoire Orchidée": ("Ivoire", "Orchidée"), "Ivoire Indigo": ("Ivoire", "Indigo"),
    "Ivoire Ebene": ("Ivoire", "Ebene"), "Ivoire Turquoise": ("Ivoire", "Turquoise"), "Turquoise Pourpre": ("Turquoise", "Pourpre"),
    "Turquoise Orchidée": ("Turquoise", "Orchidée"), "Turquoise Indigo": ("Turquoise", "Indigo"), "Turquoise Ebene": ("Turquoise", "Ebene"),
    "Prune": ("Amande Pourpre", "Amande Roux"), "Emeraude": ("Ivoire Orchidée", "Ivoire Turquoise"),
    "Prune Pourpre": ("Prune", "Pourpre"), "Prune Orchidée": ("Prune", "Orchidée"), "Prune Indigo": ("Prune", "Indigo"),
    "Prune Ebene": ("Prune", "Ebene"), "Prune Amande": ("Prune", "Amande"), "Prune Turquoise": ("Prune", "Turquoise"),
    "Prune Emeraude": ("Prune", "Emeraude"), "Emeraude Pourpre": ("Emeraude", "Pourpre"), "Emeraude Orchidée": ("Emeraude", "Orchidée"),
    "Emeraude Indigo": ("Emeraude", "Indigo"), "Emeraude Ebene": ("Emeraude", "Ebene"), "Emeraude Roux": ("Emeraude", "Roux"),
    "Emeraude Ivoire": ("Emeraude", "Ivoire"), "Emeraude Turquoise": ("Emeraude", "Turquoise"), "Emeraude Amande": ("Emeraude", "Amande"),
    "Prune Roux": ("Prune", "Roux"), "Prune Ivoire": ("Prune", "Ivoire"), "Doré": ("Prune Pourpre", "Emeraude Roux"),
    "Doré Pourpre": ("Doré", "Pourpre"), "Doré Orchidée": ("Doré", "Orchidée"), "Doré Indigo": ("Doré", "Indigo"),
    "Doré Ebene": ("Doré", "Ebene"), "Doré Roux": ("Doré", "Roux"), "Doré Amande": ("Doré", "Amande"),
    "Doré Ivoire": ("Doré", "Ivoire"), "Doré Turquoise": ("Doré", "Turquoise"), "Doré Prune": ("Doré", "Prune"),
    "Doré Emeraude": ("Doré", "Emeraude"), "Jade": ("Prune Emeraude", "Doré Pourpre"), "Rubis": ("Pourpre Emeraude", "Doré Orchidée"),
    "Saphir": ("Prune Emeraude", "Doré Indigo"), "Améthyste": ("Prune Emeraude", "Doré Ebene"), "Jade Pourpre": ("Jade", "Pourpre"),
    "Jade Orchidée": ("Jade", "Orchidée"), "Jade Indigo": ("Jade", "Indigo"), "Jade Ebene": ("Jade", "Ebene"),
    "Jade Amande": ("Jade", "Amande"), "Jade Roux": ("Jade", "Roux"), "Jade Ivoire": ("Jade", "Ivoire"),
    "Jade Turquoise": ("Jade", "Turquoise"), "Jade Prune": ("Jade", "Prune"), "Jade Emeraude": ("Jade", "Emeraude"),
    "Jade Doré": ("Jade", "Doré"), "Jade Rubis": ("Jade", "Rubis"), "Jade Saphir": ("Jade", "Saphir"),
    "Jade Améthyste": ("Jade", "Améthyste"), "Rubis Pourpre": ("Rubis", "Pourpre"), "Rubis Orchidée": ("Rubis", "Orchidée"),
    "Rubis Indigo": ("Rubis", "Indigo"), "Rubis Ebene": ("Rubis", "Ebene"), "Rubis Amande": ("Rubis", "Amande"),
    "Rubis Roux": ("Rubis", "Roux"), "Rubis Ivoire": ("Rubis", "Ivoire"), "Rubis Turquoise": ("Rubis", "Turquoise"),
    "Rubis Prune": ("Rubis", "Prune"), "Rubis Emeraude": ("Rubis", "Emeraude"), "Rubis Doré": ("Rubis", "Doré"),
    "Saphir Pourpre": ("Saphir", "Pourpre"), "Saphir Orchidée": ("Saphir", "Orchidée"), "Saphir Indigo": ("Saphir", "Indigo"),
    "Saphir Ebene": ("Saphir", "Ebene"), "Saphir Amande": ("Saphir", "Amande"), "Saphir Roux": ("Saphir", "Roux"),
    "Saphir Ivoire": ("Saphir", "Ivoire"), "Saphir Turquoise": ("Saphir", "Turquoise"), "Saphir Prune": ("Saphir", "Prune"),
    "Saphir Emeraude": ("Saphir", "Emeraude"), "Saphir Doré": ("Saphir", "Doré"), "Saphir Améthyste": ("Saphir", "Améthyste"),
    "Améthyste Pourpre": ("Améthyste", "Pourpre"), "Améthyste Orchidée": ("Améthyste", "Orchidée"), "Améthyste Indigo": ("Améthyste", "Indigo"),
    "Améthyste Ebene": ("Améthyste", "Ebene"), "Améthyste Amande": ("Améthyste", "Amande"), "Améthyste Roux": ("Améthyste", "Roux"),
    "Améthyste Ivoire": ("Améthyste", "Ivoire"), "Améthyste Turquoise": ("Améthyste", "Turquoise"), "Améthyste Prune": ("Améthyste", "Prune"),
    "Améthyste Emeraude": ("Améthyste", "Emeraude"), "Améthyste Doré": ("Améthyste", "Doré"), "Rubis Saphir": ("Rubis", "Saphir"),
    "Rubis Améthyste": ("Rubis", "Améthyste")
}

CROISEMENTS_MULDOS = {
    "Doré Pourpre": ("Doré", "Pourpre"), "Indigo Pourpre": ("Indigo", "Pourpre"), "Ebene Pourpre": ("Ebene", "Pourpre"),
    "Orchidée Pourpre": ("Orchidée", "Pourpre"), "Doré Orchidée": ("Doré", "Orchidée"), "Indigo Orchidée": ("Indigo", "Orchidée"),
    "Ebene Orchidée": ("Ebene", "Orchidée"), "Doré Indigo": ("Doré", "Indigo"), "Ebene Indigo": ("Ebene", "Indigo"),
    "Doré Ebene": ("Doré", "Ebene"), "Roux": ("Doré Pourpre", "Doré Orchidée"), "Amande": ("Indigo Pourpre", "Ebene Orchidée"),
    "Roux Pourpre": ("Roux", "Pourpre"), "Roux Orchidée": ("Roux", "Orchidée"), "Roux Indigo": ("Roux", "Indigo"),
    "Roux Ebene": ("Roux", "Ebene"), "Roux Doré": ("Roux", "Doré"), "Roux Amande": ("Roux", "Amande"),
    "Pourpre Amande": ("Pourpre", "Amande"), "Orchidée Amande": ("Orchidée", "Amande"), "Indigo Amande": ("Indigo", "Amande"),
    "Ebene Amande": ("Ebene", "Amande"), "Doré Amande": ("Doré", "Amande"), "Ivoire": ("Roux Doré", "Ebene Amande"),
    "Turquoise": ("Roux Ebene", "Doré Amande"), "Pourpre Ivoire": ("Pourpre", "Ivoire"), "Orchidée Ivoire": ("Orchidée", "Ivoire"),
    "Indigo Ivoire": ("Indigo", "Ivoire"), "Ebene Ivoire": ("Ebene", "Ivoire"), "Doré Ivoire": ("Doré", "Ivoire"),
    "Roux Ivoire": ("Roux", "Ivoire"), "Amande Ivoire": ("Amande", "Ivoire"), "Turquoise Ivoire": ("Turquoise", "Ivoire"),
    "Turquoise Pourpre": ("Turquoise", "Pourpre"), "Turquoise Indigo": ("Turquoise", "Indigo"), "Turquoise Ebene": ("Turquoise", "Ebene"),
    "Turquoise Roux": ("Turquoise", "Roux"), "Turquoise Amande": ("Turquoise", "Amande"), "Turquoise Doré": ("Turquoise", "Doré"),
    "Turquoise Orchidée": ("Turquoise", "Orchidée"), "Prune": ("Ebene Ivoire", "Turquoise Pourpre"), "Emeraude": ("Turquoise Ivoire", "Turquoise Doré"),
    "Prune Pourpre": ("Prune", "Pourpre"), "Prune Orchidée": ("Prune", "Orchidée"), "Prune Indigo": ("Prune", "Indigo"),
    "Prune Ebene": ("Prune", "Ebene"), "Prune Doré": ("Prune", "Doré"), "Prune Roux": ("Prune", "Roux"),
    "Prune Amande": ("Prune", "Amande"), "Prune Ivoire": ("Prune", "Ivoire"), "Prune Turquoise": ("Prune", "Turquoise"),
    "Prune Emeraude": ("Prune", "Emeraude"), "Orchidée Emeraude": ("Orchidée", "Emeraude"), "Indigo Emeraude": ("Indigo", "Emeraude"),
    "Ebene Emeraude": ("Ebene", "Emeraude"), "Doré Emeraude": ("Doré", "Emeraude"), "Roux Emeraude": ("Roux", "Emeraude"),
    "Amande Emeraude": ("Amande", "Emeraude"), "Ivoire Emeraude": ("Ivoire", "Emeraude"), "Turquoise Emeraude": ("Turquoise", "Emeraude"),
    "Pourpre Emeraude": ("Pourpre", "Emeraude"), "Ambre": ("Pourpre Emeraude", "Roux Emeraude"), "Corail": ("Prune Pourpre", "Prune Roux"),
    "Azur": ("Pourpre Emeraude", "Prune Roux"), "Aigue-Marine": ("Prune Pourpre", "Roux Emeraude"), "Ambre Doré": ("Ambre", "Doré"),
    "Ambre Ebene": ("Ambre", "Ebene"), "Ambre Indigo": ("Ambre", "Indigo"), "Ambre Pourpre": ("Ambre", "Pourpre"),
    "Ambre Orchidée": ("Ambre", "Orchidée"), "Ambre Amande": ("Ambre", "Amande"), "Ambre Roux": ("Ambre", "Roux"),
    "Ambre Ivoire": ("Ambre", "Ivoire"), "Ambre Turquoise": ("Ambre", "Turquoise"), "Ambre Emeraude": ("Ambre", "Emeraude"),
    "Ambre Prune": ("Ambre", "Prune"), "Ambre Corail": ("Ambre", "Corail"), "Ambre Azur": ("Ambre", "Azur"),
    "Ambre Aigue-Marine": ("Ambre", "Aigue-Marine"), "Corail Doré": ("Corail", "Doré"), "Corail Ebene": ("Corail", "Ebene"),
    "Corail Indigo": ("Corail", "Indigo"), "Corail Pourpre": ("Corail", "Pourpre"), "Corail Orchidée": ("Corail", "Orchidée"),
    "Corail Amande": ("Corail", "Amande"), "Corail Roux": ("Corail", "Roux"), "Corail Ivoire": ("Corail", "Ivoire"),
    "Corail Turquoise": ("Corail", "Turquoise"), "Corail Emeraude": ("Corail", "Emeraude"), "Corail Prune": ("Corail", "Prune"),
    "Corail Azur": ("Corail", "Azur"), "Corail Aigue-Marine": ("Corail", "Aigue-Marine"), "Azur Doré": ("Azur", "Doré"),
    "Azur Ebene": ("Azur", "Ebene"), "Azur Indigo": ("Azur", "Indigo"), "Azur Pourpre": ("Azur", "Pourpre"),
    "Azur Orchidée": ("Azur", "Orchidée"), "Azur Amande": ("Azur", "Amande"), "Azur Roux": ("Azur", "Roux"),
    "Azur Ivoire": ("Azur", "Ivoire"), "Azur Turquoise": ("Azur", "Turquoise"), "Azur Emeraude": ("Azur", "Emeraude"),
    "Azur Prune": ("Azur", "Prune"), "Azur Aigue-Marine": ("Azur", "Aigue-Marine"), "Aigue-Marine Doré": ("Aigue-Marine", "Doré"),
    "Aigue-Marine Ebene": ("Aigue-Marine", "Ebene"), "Aigue-Marine Indigo": ("Aigue-Marine", "Indigo"), "Aigue-Marine Pourpre": ("Aigue-Marine", "Pourpre"),
    "Aigue-Marine Orchidée": ("Aigue-Marine", "Orchidée"), "Aigue-Marine Amande": ("Aigue-Marine", "Amande"), "Aigue-Marine Roux": ("Aigue-Marine", "Roux"),
    "Aigue-Marine Ivoire": ("Aigue-Marine", "Ivoire"), "Aigue-Marine Turquoise": ("Aigue-Marine", "Turquoise"), "Aigue-Marine Emeraude": ("Aigue-Marine", "Emeraude"),
    "Aigue-Marine Prune": ("Aigue-Marine", "Prune")
}

class MenuScreen(Screen):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        layout = BoxLayout(orientation='vertical', padding=20, spacing=20)
        titre = Label(text="Généalogie Dofus - Élevage", font_size='22sp', bold=True, size_hint_y=0.3)
        layout.add_widget(titre)

        btn_dd = Button(text="Dragodinde", background_color=get_color_from_hex("#d35400"), font_size='18sp')
        btn_dd.bind(on_press=lambda x: self.ouvrir_espece("Dragodinde"))
        layout.add_widget(btn_dd)

        btn_vk = Button(text="Volkorne", background_color=get_color_from_hex("#8e44ad"), font_size='18sp')
        btn_vk.bind(on_press=lambda x: self.ouvrir_espece("Volkorne"))
        layout.add_widget(btn_vk)

        btn_ml = Button(text="Muldo", background_color=get_color_from_hex("#27ae60"), font_size='18sp')
        btn_ml.bind(on_press=lambda x: self.ouvrir_espece("Muldo"))
        layout.add_widget(btn_ml)

        self.add_widget(layout)

    def ouvrir_espece(self, espece):
        plan_screen = self.manager.get_screen('plan')
        plan_screen.set_espece(espece)
        self.manager.current = 'plan'

class PlanScreen(Screen):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.espece_actuelle = "Dragodinde"
        self.main_layout = BoxLayout(orientation='vertical', padding=10, spacing=10)

        header = BoxLayout(size_hint_y=0.1, spacing=10)
        self.titre = Label(text="Plan d'Élevage", font_size='18sp', bold=True)
        btn_retour = Button(text="Retour", size_hint_x=0.3, background_color=get_color_from_hex("#555555"))
        btn_retour.bind(on_press=self.retour_menu)
        header.add_widget(self.titre)
        header.add_widget(btn_retour)
        self.main_layout.add_widget(header)

        self.spinner = Spinner(text='Choisir une monture', size_hint_y=0.1)
        self.main_layout.add_widget(self.spinner)

        btn_generer = Button(text="Générer les étapes", size_hint_y=0.1, background_color=get_color_from_hex("#2f80ed"))
        btn_generer.bind(on_press=self.generer_plan)
        self.main_layout.add_widget(btn_generer)

        self.scroll = ScrollView(size_hint=(1, 0.5))
        self.etapes_layout = BoxLayout(orientation='vertical', size_hint_y=None, spacing=5)
        self.etapes_layout.bind(minimum_height=self.etapes_layout.setter('height'))
        self.scroll.add_widget(self.etapes_layout)
        self.main_layout.add_widget(self.scroll)

        self.lbl_resume = Label(text="Sélectionnez une monture.", size_hint_y=0.2, font_size='14sp', halign='left', valign='top')
        self.lbl_resume.bind(size=self.lbl_resume.setter('text_size'))
        self.main_layout.add_widget(self.lbl_resume)

        self.add_widget(self.main_layout)

    def retour_menu(self, instance):
        self.manager.current = 'menu'

    def set_espece(self, espece):
        self.espece_actuelle = espece
        self.titre.text = f"Élevage - {espece}"
        dico = self.get_dico_actif()
        self.spinner.values = sorted(list(dico.keys()))
        self.spinner.text = "Choisir une monture"
        self.etapes_layout.clear_widgets()
        self.lbl_resume.text = "En attente de génération..."

    def get_dico_actif(self):
        if self.espece_actuelle == "Dragodinde": return CROISEMENTS_DRAGODINDES
        elif self.espece_actuelle == "Volkorne": return CROISEMENTS_VOLKORNES
        else: return CROISEMENTS_MULDOS

    def calculer_generation(self, monture, dico):
        if monture not in dico: return 1
        p1, p2 = dico[monture]
        return max(self.calculer_generation(p1, dico), self.calculer_generation(p2, dico)) + 1

    def generer_plan(self, instance):
        self.etapes_layout.clear_widgets()
        cible = self.spinner.text
        if cible == "Choisir une monture": return

        dico_actif = self.get_dico_actif()
        self.compteur_pures = {}
        montures_requises = set()

        def trouver_requis(m):
            if m in dico_actif:
                montures_requises.add(m)
                p1, p2 = dico_actif[m]
                trouver_requis(p1)
                trouver_requis(p2)
            else:
                self.compteur_pures[m] = self.compteur_pures.get(m, 0) + 1

        trouver_requis(cible)

        etapes = {}
        for m in montures_requises:
            gen = self.calculer_generation(m, dico_actif)
            if gen not in etapes: etapes[gen] = []
            etapes[gen].append(m)

        for gen in sorted(etapes.keys()):
            is_final = (gen == max(etapes.keys()))
            nom_etape = f"--- 🏁 Étape Finale (Gén. {gen}) ---" if is_final else f"--- 🧬 Étape {gen-1} (Pour Gén. {gen}) ---"
            
            lbl_e = Label(text=nom_etape, size_hint_y=None, height=30, color=(1, 0.8, 0, 1), bold=True)
            self.etapes_layout.add_widget(lbl_e)

            for m in sorted(etapes[gen]):
                p1, p2 = dico_actif[m]
                texte = f"[{p1}] + [{p2}] => {m}"
                lbl_c = Label(text=texte, size_hint_y=None, height=25, font_size='12sp')
                self.etapes_layout.add_widget(lbl_c)

        texte_resume = "📊 Pures nécessaires :\n"
        total = 0
        for race, qte in sorted(self.compteur_pures.items()):
            texte_resume += f"• {qte}x {race}  "
            total += qte
        texte_resume += f"\nTotal : {total} pures"
        self.lbl_resume.text = texte_resume

class ElevageApp(App):
    def build(self):
        sm = ScreenManager()
        sm.add_widget(MenuScreen(name='menu'))
        sm.add_widget(PlanScreen(name='plan'))
        return sm

if __name__ == '__main__':
    ElevageApp().run()
