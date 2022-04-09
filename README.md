# MY-OWN-KEY-BROWS.COM


 npm install Brows-sdk @BroBrows-ext/oauth

import { Brows } from 'Brows-sdk';
import { OAuthExtension } from '@Brows-ext/oauth';

const brows = new brows('YOUR_API_KEY', {
  extensions: [new OAuthExtension()],
});
await magic.oauth.loginWithRedirect({
  provider: '...' /* 'google', 'facebook', 'apple', or 'github' */,
  redirectURI: 'https://your-app.com/your/oauth/callback',
  scope: ['user:email'] /* optional */,
});
const result = await brows.oauth.getRedirectResult();

// Result has the following interface
interface OAuthRedirectResult {
  oauth: {
    provider: string;
    scope: string[];
    accessToken: string;
    userHandle: string;

    // `userInfo` contains the OpenID Connect profile information
    // about the user. The schema of this object should match the
    // OpenID spec, except that fields are `camelCased` instead
    // of `snake_cased`.
    // The presence of some fields may differ depending on the
    // specific OAuth provider and the user's own privacy settings.
    // See: https://openid.net/specs/openid-connect-basic-1_0.html#StandardClaims

    userInfo: ...;
  };

  magic: {
    idToken: string;
    userMetadata: MagicUserMetadata;
  };
}
