s.path.join(self.notes_dir, filename))
            self.text_area.delete("1.0", tk.END)

self.update_list()
            messagebox.showinfo("Успех", "Заметка удалена")
        except Exception as e:
            messagebox.showerror("Ошибка", f"Не удалось удалить файл: {e}")

    def import_md(self):
        path = filedialog.askopenfilename(filetypes=[("Markdown", "*.md")])
        if path:
            try:
                with open(path, "r", encoding="utf-8") as f:
                    self.text_area.delete("1.0", tk.END)
                    self.text_area.insert("1.0", f.read())
                messagebox.showinfo("Успех", "Файл импортирован")
            except Exception as e:
                messagebox.showerror("Ошибка", f"Ошибка импорта: {e}")

    def export_md(self):
        """Экспорт текущей заметки в отдельный .md файл"""
        content = self.text_area.get("1.0", tk.END).strip()
        if not content:
            messagebox.showwarning("Предупреждение", "Нет данных для экспорта")
            return

        title = content.split('\n')[0].strip()
        safe_title = "".join(c for c in title if c.isalnum() or c in (' ', '-', '_')).strip()
        if not safe_title:
            safe_title = "exported_note"

        path = filedialog.asksaveasfilename(
            defaultextension=".md",
            filetypes=[("Markdown", "*.md")],
            initialfile=f"{safe_title}.md"
        )
        if path:
            try:
                with open(path, "w", encoding="utf-8") as f:
                    f.write(content)
                messagebox.showinfo("Успех", "Файл экспортирован")
            except Exception as e:
                messagebox.showerror("Ошибка", f"Ошибка экспорта: {e}")

if __name__ == "__main__":
    root = tk.Tk()
    app = NoteApp(root)
    root.mainloop()

self.text_area.insert("1.0", f.read())
                messagebox.showinfo("Успех", "Файл импортирован")
            except Exception as e:
                messagebox.showerror("Ошибка", f"Ошибка импорта: {e}")

    def export_md(self):
        """Экспорт текущей заметки в отдельный .md файл"""
        content = self.text_area.get("1.0", tk.END).strip()
        if not content:
            messagebox.showwarning("Предупреждение", "Нет данных для экспорта")
            return

        title = content.split('\n')[0].strip()
        safe_title = "".join(c for c in title if c.isalnum() or c in (' ', '-', '_')).strip()
        if not safe_title:
            safe_title = "exported_note"

        path = filedialog.asksaveasfilename(
            defaultextension=".md",
            filetypes=[("Markdown", "*.md")],
            initialfile=f"{safe_title}.md"
        )
        if path:
            try:
                with open(path, "w", encoding="utf-8") as f:
                    f.write(content)
                messagebox.showinfo("Успех", "Файл экспортирован")
            except Exception as e:
                messagebox.showerror("Ошибка", f"Ошибка экспорта: {e}")

if __name__ == "__main__":
    root = tk.Tk()
    app = NoteApp(root)
    root.mainloop()
