export default async function handler(req, res) {
  const text = req.query.text || '';
  const url = `https://translate.google.com/translate_tts?ie=UTF-8&q=${encodeURIComponent(text)}&tl=ko&client=tw-ob`;

  const response = await fetch(url, {
    headers: {
      'User-Agent':
        'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 Chrome/100 Safari/537.36',
    },
  });

  if (!response.ok) {
    res.status(500).send('TTS fetch failed');
    return;
  }

  res.setHeader('Content-Type', 'audio/mpeg');
  const buffer = await response.arrayBuffer();
  res.send(Buffer.from(buffer));
}
