let latestTeleport = "";

export default async function handler(req, res) {
  if (req.method === "POST") {
    const body = req.body;
    if (body.teleport) {
      latestTeleport = body.teleport;
      console.log("Updated teleport:", latestTeleport);
      return res.status(200).json({ message: "Teleport command updated." });
    } else {
      return res.status(400).json({ error: "Missing teleport field." });
    }
  } else if (req.method === "GET") {
    return res.status(200).json({ teleport: latestTeleport });
  } else {
    return res.status(405).json({ error: "Method not allowed." });
  }
}
