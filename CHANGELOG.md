# Changelog (douglasreiswebjs fork)

This fork carries targeted fixes on top of upstream `whatsapp-web.js`.

## 1.34.13
- Force-ready fallback after `authenticated` and at 99% loading to avoid stuck readiness.
- Add safety wait for Store.Msg and minimal WWebJS utils when injection stalls.
- Retry ready emission if initial store injection does not complete.

## 1.34.12
- Add node-side message dedupe to prevent duplicate `message` events when WA emits multiple internal signals.
- Keep existing message fallbacks and polling but ensure only one emit per message id within a short TTL.

## 1.34.11
- Guard group metadata update to avoid `TypeError: Cannot read properties of undefined (reading 'update')` in `getChatModel`.
- Fallback to alternate GroupQuery/GroupMetadata update paths when the primary update hook is missing.

## 1.34.10
- Expand message detection fallbacks: Store.Msg/Chat polling, unreadCount, lastReceivedKey.
- Normalize message model extraction and handle ciphertext transitions more reliably.

## 1.34.9
- Relax “new message” detection (isNewMsg/isNew/isUnread/recent) to handle WA layout changes.

## 1.34.8
- Retry ready/auth attach sequence until Store/WWebJS/Msg is available.
- Guard against duplicate authenticated/ready emission.

## 1.34.7
- Ensure event listeners attach only once per page context; add guards for re-injection.

## 1.34.6
- If AppState reports CONNECTED or loading >= 99, treat as synced and fire sync event.

## 1.34.5
- Improve loading-screen completion and retry logic to avoid stuck 99%.

## 1.34.4
- Mark loading screen as finished at 100% to prevent repeated loading updates.

## 1.34.3
- Fix AppState `hasSynced` handling to properly emit sync event on initialization.
