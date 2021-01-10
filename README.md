# stable-demo

Hey hey!

I used Vue to build this app, since I am the most familiar with it. It took about 3 hours, but I spent over half of the time fiddling with CSS. In case the app is hard to decipher coming from react, I'll explain the application here. Starting from layouts/default.vue you see there is a navbar, a divider, and then the Nuxt component. Nuxt is the best Vue project framework and it puts the majority of the app in this Nuxt component. So in this case, Nuxt is just pages/index.vue. Index.vue contains the greeting message, the grid of mail cards, and the navigation buttons. components/MailCard.vue is, surprise, where the MailCard component lives. This componenent is a bit lengthy because of all the conditionals I put into it. One could definitely make this more concise by abstracting away the conditional icon/label bits into individual components, but IMO its more readable this way. Also, I just copypasted the image asset urls for the icons. In a real app I would probably use bootstrap-icons or some other global css style reference.

You will notice that the app doesn't look EXACTLY like the mockup. Notably the card footer comes with a gray background in bootstrap-vue and NotoSans is not the font used in the mockup. I hope that's alright. The other change I should mention is the user can resize the window to allow more than 3 items per row, and shrink it to allow fewer than 3. At 100% window zoom it defaults to 3 items per row.

You can play with the hosted version here: http://stabledemo-env.eba-r8na3cqm.us-east-2.elasticbeanstalk.com/

If you want to run the app locally, follow the steps below.

## Build Setup

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).
