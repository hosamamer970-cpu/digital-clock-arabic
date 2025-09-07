import tkinter as tk
from tkinter import ttk
from datetime import datetime
try:
    # Python 3.9+
    from zoneinfo import ZoneInfo
    CAIRO_TZ = ZoneInfo("Africa/Cairo")
except Exception:
    CAIRO_TZ = None  # fallback على توقيت الجهاز لو مافيش zoneinfo

# أسماء الأيام والشهور بالعربي
AR_DAYS = ["الاثنين","الثلاثاء","الأربعاء","الخميس","الجمعة","السبت","الأحد"]
AR_MONTHS = [
    "يناير","فبراير","مارس","أبريل","مايو","يونيو",
    "يوليو","أغسطس","سبتمبر","أكتوبر","نوفمبر","ديسمبر"
]

class DigitalClock(tk.Tk):
    def __init__(self):
        super().__init__()
        self.title("ساعة رقمية")
        self.geometry("480x260")
        self.resizable(False, False)

        # حالات
        self.use_24h = tk.BooleanVar(value=True)
        self.always_on_top = tk.BooleanVar(value=False)
        self.dark_mode = tk.BooleanVar(value=True)
        self._blink_state = True  # عشان وميض النقطتين

        # ألوان للثيمين
        self.colors = {
            "dark": {
                "bg": "#0f1115",
                "card": "#151823",
                "text_primary": "#e6e6e6",
                "text_secondary": "#a6adbb",
                "accent": "#7dd3fc"
            },
            "light": {
                "bg": "#f6f7fb",
                "card": "#ffffff",
                "text_primary": "#1f2937",
                "text_secondary": "#6b7280",
                "accent": "#2563eb"
            }
        }

        self._build_ui()
        self._apply_theme()
        self.update_clock()

    def _build_ui(self):
        # الإطار الرئيسي (كارت)
        self.card = tk.Frame(self, bd=0, highlightthickness=0)
        self.card.place(relx=0.5, rely=0.5, anchor="center", width=450, height=210)

        # الوقت الكبير
        self.time_label = tk.Label(self.card, text="00:00:00", font=("Segoe UI", 46, "bold"))
        self.time_label.pack(pady=(18, 2))

        # التاريخ واليوم
        self.date_label = tk.Label(self.card, text="السبت، 1 يناير 2025", font=("Segoe UI", 14))

        self.date_label.pack(pady=(0, 8))

        # صف التحكمات
        controls = tk.Frame(self.card, bd=0, highlightthickness=0)
        controls.pack(pady=(6, 0))

        # 12/24
        self.toggle_24h = ttk.Checkbutton(
            controls, text="نظام 24 ساعة", variable=self.use_24h, command=self._refresh_once
        )
        self.toggle_24h.grid(row=0, column=0, padx=6)

        # Always on top
        self.toggle_top = ttk.Checkbutton(
            controls, text="دائمً


