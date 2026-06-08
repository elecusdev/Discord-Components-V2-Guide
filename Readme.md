# Discord Sunucumuz (Star Vererek Destek Olabilirsiniz)
[![Discord Banner](https://api.weblutions.com/discord/invite/codeworld/)](https://discord.gg/codeworld)

----

# 🚀 Elecus Development - Discord Components V2 Rehberi

> Modern Discord botları için yeni nesil Components V2 kullanım rehberi.
>
> Discord.js v14 ile geliştirilen Elecus Development altyapısı sayesinde embed kullanmadan profesyonel ve etkileşimli mesajlar oluşturabilirsiniz.

---

# 📌 Components V2 Nedir?

Components V2, Discord'un yeni mesaj sistemidir.

Bu sistem sayesinde:

✅ Embed kullanmadan modern arayüzler oluşturabilirsiniz

✅ Butonlar ve seçim menüleri ekleyebilirsiniz

✅ Galeri ve medya gösterimleri yapabilirsiniz

✅ Dosya paylaşabilirsiniz

✅ Bilgileri profesyonel şekilde kategorilere ayırabilirsiniz

✅ Mobil ve masaüstünde daha temiz görünüm elde edebilirsiniz

---

# 📝 TextDisplay

Statik metin göstermek için kullanılır.

```js
const { TextDisplayBuilder } = require('discord.js');

const textDisplay = new TextDisplayBuilder()
    .setContent('🚀 Elecus Development Components V2 Sistemi');
```

---

# ➖ Separator

Bileşenler arasında boşluk veya ayırıcı oluşturur.

```js
const {
    SeparatorBuilder,
    SeparatorSpacingSize
} = require('discord.js');

const separator = new SeparatorBuilder()
    .setDivider(true)
    .setSpacing(SeparatorSpacingSize.Small);
```

---

# 📂 Section

İçerikleri düzenli şekilde gruplamak için kullanılır.

```js
const {
    SectionBuilder,
    TextDisplayBuilder,
    ThumbnailBuilder
} = require('discord.js');

const section = new SectionBuilder()
    .addTextDisplayComponents(
        new TextDisplayBuilder()
            .setContent('📂 Sunucu Yönetimi'),

        new TextDisplayBuilder()
            .setContent('Elecus Development yönetim paneli.')
    )
    .setThumbnailAccessory(
        new ThumbnailBuilder({
            media: {
                url: 'https://cdn.elecus.link/logo.png'
            }
        })
    );
```

---

# 🖼️ Thumbnail

Section bileşenlerine küçük görsel ekler.

```js
const { ThumbnailBuilder } = require('discord.js');

const thumbnail = new ThumbnailBuilder({
    media: {
        url: 'https://cdn.elecus.link/logo.png'
    }
});
```

---

# 🔘 Button

Kullanıcılarla etkileşim kurmak için kullanılır.

```js
const {
    ButtonBuilder,
    ButtonStyle
} = require('discord.js');

const websiteButton = new ButtonBuilder()
    .setLabel('Elecus Website')
    .setURL('https://elecus.link')
    .setStyle(ButtonStyle.Link);
```

---

# 📋 Channel Select Menu

Kanal seçim menüsü oluşturur.

```js
const {
    ChannelSelectMenuBuilder
} = require('discord.js');

const channelMenu = new ChannelSelectMenuBuilder()
    .setCustomId('elecus_channel_menu')
    .setPlaceholder('Bir kanal seçiniz...');
```

---

# 🖼️ Media Gallery

Birden fazla görsel veya videoyu galeri şeklinde gösterir.

```js
const {
    MediaGalleryBuilder,
    MediaGalleryItemBuilder
} = require('discord.js');

const gallery = new MediaGalleryBuilder()
    .addItems(
        new MediaGalleryItemBuilder()
            .setURL('https://cdn.elecus.link/showcase1.png'),

        new MediaGalleryItemBuilder()
            .setURL('https://cdn.elecus.link/showcase2.png')
    );
```

---

# 📄 File Component

Dosya paylaşımı için kullanılır.

```js
const {
    AttachmentBuilder,
    FileBuilder
} = require('discord.js');

const attachment = new AttachmentBuilder('./data/config.json')
    .setName('config.json');

const fileComponent = new FileBuilder()
    .setURL('attachment://config.json');
```

---

# 📦 Container

Tüm bileşenleri tek yapı içerisinde toplar.

```js
const {
    ContainerBuilder,
    TextDisplayBuilder
} = require('discord.js');

const container = new ContainerBuilder()
    .setAccentColor(0x5865F2)
    .addTextDisplayComponents(
        new TextDisplayBuilder()
            .setContent('💙 Elecus Development')
    );
```

---

# 🔥 Tam Components V2 Örneği

```js
const {
    SlashCommandBuilder,
    MessageFlags,
    ContainerBuilder,
    TextDisplayBuilder,
    SeparatorBuilder,
    SeparatorSpacingSize,
    SectionBuilder,
    ThumbnailBuilder,
    MediaGalleryBuilder,
    MediaGalleryItemBuilder,
    ButtonBuilder,
    ButtonStyle
} = require('discord.js');

module.exports = {
    data: new SlashCommandBuilder()
        .setName('elecus')
        .setDescription('Elecus Development tanıtım paneli'),

    async execute(interaction, client) {

        const avatar = client.user.displayAvatarURL({
            extension: 'png',
            size: 1024
        });

        const container = new ContainerBuilder()
            .setAccentColor(0x5865F2)

            .addTextDisplayComponents(
                new TextDisplayBuilder()
                    .setContent('# 🚀 Elecus Development')
            )

            .addSeparatorComponents(
                new SeparatorBuilder()
                    .setDivider(true)
                    .setSpacing(SeparatorSpacingSize.Small)
            )

            .addSectionComponents(
                new SectionBuilder()
                    .addTextDisplayComponents(
                        new TextDisplayBuilder()
                            .setContent('### 🌍 Modern Discord Çözümleri'),

                        new TextDisplayBuilder()
                            .setContent(
                                'Bot sistemleri, web panelleri, API servisleri ve özel yazılım çözümleri.'
                            )
                    )
                    .setThumbnailAccessory(
                        new ThumbnailBuilder({
                            media: {
                                url: avatar
                            }
                        })
                    )
            )

            .addMediaGalleryComponents(
                new MediaGalleryBuilder()
                    .addItems(
                        new MediaGalleryItemBuilder()
                            .setURL(avatar)
                    )
            )

            .addSectionComponents(
                new SectionBuilder()
                    .addTextDisplayComponents(
                        new TextDisplayBuilder()
                            .setContent('🌐 Resmi Web Sitesi')
                    )
                    .setButtonAccessory(
                        new ButtonBuilder()
                            .setLabel('elecus.link')
                            .setURL('https://elecus.link')
                            .setStyle(ButtonStyle.Link)
                    )
            )

            .addTextDisplayComponents(
                new TextDisplayBuilder()
                    .setContent('## Özellikler'),

                new TextDisplayBuilder()
                    .setContent('• Components V2'),

                new TextDisplayBuilder()
                    .setContent('• Discord.js v14'),

                new TextDisplayBuilder()
                    .setContent('• Modern UI Tasarımları'),

                new TextDisplayBuilder()
                    .setContent('• Hızlı ve Güvenli Sistemler'),

                new TextDisplayBuilder()
                    .setContent('• Elecus Development Altyapısı')
            );

        await interaction.reply({
            flags: MessageFlags.IsComponentsV2,
            components: [container]
        });
    }
};
```

---

# 💡 En İyi Kullanım Önerileri

- Gereksiz uzun içeriklerden kaçının.
- Mobil kullanıcıları düşünerek tasarım yapın.
- Bölümleri Separator ile ayırın.
- Linkler için Button kullanın.
- Galeri gösterimleri için MediaGallery tercih edin.
- Tüm sistemleri Container içinde toplayın.

---

# 🌐 Elecus Development

Modern Discord sistemleri, özel bot projeleri ve gelişmiş altyapılar.

**Website:** https://elecus.dev

**Marka:** Elecus Development

**Teknoloji:** Discord.js v14 + Components V2

---

![Components Preview](https://repository-images.githubusercontent.com/1038141980/c0761e9e-aebb-4ed6-885c-f74a30ffc3fd)
