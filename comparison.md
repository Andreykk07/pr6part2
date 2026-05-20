# Порівняльний аналіз моделей: GPT-4o vs Claude 3.5 Sonnet

Для тестування моделей та нашого системного промпту було використано завідомо вразливий та неоптимальний код Express роутера:

```javascript
router.post('/update-profile', async (req, res) => {
  var user = await db.query("SELECT * FROM users WHERE id = " + req.body.id);
  if (user) {
    for (let i = 0; i < req.body.wishes.length; i++) {
      await db.query("INSERT INTO wishes (user_id, text) VALUES (" + req.body.id + ", '" + req.body.wishes[i] + "')");
    }
    res.send({ status: "ok" });
  }
});
