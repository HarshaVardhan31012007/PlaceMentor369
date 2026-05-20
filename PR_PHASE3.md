# feat(student): (Phase 3) title

## Summary

This pull request implements **Phase 3: Background Queue Integration**. The AI resume parsing is now performed in a BullMQ queue backed by Redis, preventing the main Express thread from blocking.

## What changed
- **BullMQ & ioredis** installed and configured.
- **`backend/workers/aiWorker.js`** added – runs the Gemini extraction in the background.
- **Redis config** (`backend/config/redis.js`) reads the connection string from `process.env.REDIS_URI`.
- **`uploadResume` controller** now enqueues a job and immediately returns **202 Accepted**.
- **Graceful fallback** to synchronous processing when Redis is unavailable.
- Front‑end shows a fast "processing" toast, ready for real‑time updates in Phase 4.

## Admin Note – **Set the Redis URL**

The queue will only start when a valid Redis connection string is provided via the environment variable **`REDIS_URI`**.

1. Open (or create) the `.env` file at the project root:
   ```
   c:/Users/harsha/Downloads/PlaceMentor369/.env
   ```
2. Add the following line (replace the host/port/password as necessary):
   ```
   REDIS_URI=redis://localhost:6379
   ```
   - For password‑protected Redis:
     ```
     REDIS_URI=redis://:YOUR_PASSWORD@your-redis-host:6379
     ```
3. Save the file and restart the development server (`npm run dev`). You should see:
   ```
   ✅ Redis Connected successfully
   👷 Starting BullMQ Worker: ai-analysis-queue
   ```
⚠️ **Important:** After updating `REDIS_URI`, stop the running server and start it again (or reload) for the new Redis connection to take effect.
If `REDIS_URI` is missing or incorrect, the worker will not start and the controller will fall back to the old synchronous flow.

## Verification Plan
1. Ensure Redis server is running and `REDIS_URI` is set.
2. Run `npm run dev` – look for the logs above.
3. Upload a resume via the frontend – you should receive an immediate **202** response.
4. Observe the worker logs confirming job completion. **Note:** The frontend shows a success toast instantly, but the updated profile information will appear only after the page is refreshed or the data is refetched.


## Screenshots
Below are the screenshots you should add to illustrate the new flow. Replace the placeholder paths with the actual image files you capture.

> **Upload Resume – Immediate 202 Response**
> ![Upload success toast](file:///c:/Users/harsha/Downloads/PlaceMentor369/screenshot_upload_toast.png)
>
> **Server console – Redis connected & worker started**
> ![Server start logs](file:///c:/Users/harsha/Downloads/PlaceMentor369/screenshot_server_logs.png)
>
> **BullMQ worker processing job**
> ![Worker processing](file:///c:/Users/harsha/Downloads/PlaceMentor369/screenshot_worker.png)
>
> *Add any additional screenshots that demonstrate the UI and backend behavior.*

## Closes
- Part of #68

## Checklist
- [x] Participating via GSSoC
- [x] Followed contribution guidelines
- [x] Code style adhered to
- [x] Self‑review completed
